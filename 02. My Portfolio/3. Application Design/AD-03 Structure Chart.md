***Dashboard generation***

At the top of the hierarchy is the Generate Dashboard module, which coordinates all submodules to retrieve, process, and present the user's sleep data. It delegates to four key retrieval modules: Get User Data (retrieves the current user from the database using `session['user_id']`), Get Sleep Entries (retrieves the user's most recent entries and passes them to Calculate Statistics), Get Sleep Goal (retrieves the user's target hours if set), and Get Quote (calls the ZenQuotes API via Fetch ZenQuotes API, with a fallback if unavailable).

Once data is retrieved and processed, the results are passed to the Jinja2 template renderer to produce the final dashboard HTML response.

**Algorithm**
	`BEGIN GenerateDashboard
	    `user = GetUserData(session['user_id'])
	    `entries = GetSleepEntries(session['user_id'])
	    `goal = GetSleepGoal(session['user_id'])
	    `quote, author = GetQuote()
	
	    stats = CalculateStatistics(entries)
	
	    IF entries is empty
	        DISPLAY "Log your first sleep entry to see your stats!"
	    ELSE
	        DISPLAY stats.avg_duration, stats.avg_quality, stats.last_quality
	    ENDIF
	
	    DISPLAY quote, author
	    IF goal is not None
	        DISPLAY goal.target_hours
	    ENDIF
	END
	
	
	BEGIN GetSleepEntries(user_id)
	    query = SELECT SleepEntry WHERE user_id = user_id ORDER BY bedtime DESC LIMIT 7
	    entries = ExecuteQuery(query)
	    RETURN entries
	END
	
	
	BEGIN CalculateStatistics(entries)
	    IF entries is empty
	        RETURN empty stats
	    ENDIF
	
	    total_duration = 0
	    total_quality = 0
	
	    FOR entry IN entries
	        total_duration = total_duration + entry.calculate_duration()
	        total_quality = total_quality + entry.quality
	    ENDFOR
	
	    avg_duration = ROUND(total_duration / LENGTH(entries), 1)
	    avg_quality = ROUND(total_quality / LENGTH(entries), 1)
	    last_quality = entries[0].quality_label
	
	    RETURN avg_duration, avg_quality, last_quality
	END

***Log sleep flowchart***

![[02. My Portfolio/3. Application Design/Logsleepchart.drawio.png]]

The Log Sleep flowchart shows the process executed when a user submits the `/log` form. The form is first validated by Flask-WTF (CSRF check, required fields, data types). If validation fails, the form is re-rendered with error messages. If valid, the `notes` field is sanitised using `sanitise()` to strip HTML tags, the custom `validate_wake_time()` check confirms `wake_time > bedtime`, the `SleepEntry` is committed to the database, and the user is redirected to their sleep history with a success flash message.