1. to start claude session
    $ claude --model claude-sonnet-4-5-20250929
2. to retrive previous sessions
    $ claude -r --model claude-sonnet-4-5-20250929
3. one session to anothe previous session
    /resume
4. Switch between models
    /model
5. to get the top-up done
    /extra-usage
6. provides statistics based on usage
    /stats

best practices:
1. One session = one task
2. Name your session
    /rename <name> (run inside a session)
3. Commit frequently within a session
4. use /btw for quick questions
5. Export a session before 
    /export <newfilename>
    we can export our chats using export command, later we can use this to provide context

models:
1. opus - most powerful and expensive
    planning phase - thinking through architecture, writting specs, making decissions
2. sonnet - Best in speed, quality and token cost
    Implementation phase - where planning is done
3. haiku - fast and cheap
    use - simple, repeatative or exploratory tasks where dont need deep reasoning

