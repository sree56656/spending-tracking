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

=================== Context window =======================
1. claudecode context window - 200k tokens (actual 150k tokens only)
2. claude replies(o/p) consumes 6x more tokens than input
3. Auto compaction (33k tokens reserved) - once hits 200k token it summerizes and saves in auto compact, it triggers at (75-92% full), once 33k fills then hard stops the session
4. /context gives current usage
5. Response quality degrades as context fills up
6. /compact --> manual auto compaction
    ctrl + o --> to see conpact summary

    1. one session per feature
    2. use /compact before claude runs compaction
    3. write focused and specific prompts
    4. Use subagents for Isolated or exploratory work
    5. use .claudeignore to keep irrelevant files out

    ========= CLAUDE.md file ===================

7. LLMs dont have memory
8. claude code cant remember things from prev sessions
9. Need to repeat instraructuions across solutions - CLAUDE.md
10. CLAUDE.md ==> 1. your project level instruction file
                  2. claude code automatically reads this file in each session
                  3. Create manually or using /init (preffered)
                  4. /init - triggers an internal agent that takes over the scanning and writting

11. .claude folder ==> tools box for the project
    Global/User-level ~/.claude/ ==> scoped to local machine, applied to every proj
12. claude.local.md(personal) => can add in proj folder but it wont be added to git by default
13. make sure claude.md < 200 lines. steps to reduce the size of claude.md file
            1. .claude/rules/<name>.md  ==> can create multiple files (not loads automatically)
                                            loads only when it is required

            2. Use @imports to reference external docs
                            ## API Conventions
                            see @docs/api-guidelines.md
                            ## Git Workflow
                            see @docs/contributing.md

            3. Use sub directory claude.md

====== Auto memory (Memory.md)===========

1. It is a persistant memory where claude records learnings, patterns and its insights as it works.
2. along with claude.md memory.md(top 200 lines only) also loads
3. memory stores in ~/.claude/projects/<project>/memory
4. update your memory files - We use INR not USD
    /memory
