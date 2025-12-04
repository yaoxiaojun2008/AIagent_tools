This is simple agent example.
It connects to Gemini LLM and provides 3 tools to read, write, list files.
It starts in a loop way, wait for user input, if users request to list a directory, LLM returns the tool name, then agent to run the tool and integrity the tool output to LLM to give final response.
When agent starts, it passes tools list to LLM by config parameter.
