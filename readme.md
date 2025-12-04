This is a simple agent example.
It connects to Gemini LLM and provides 3 tools to read, write, list files.
It starts in a loop way, waits for users input, if users request to list a directory, LLM returns the tool name, then agent is to run the tool and integrate the tool's outputs into the prompt, then LLM  gives the final response.
When the agent starts, it passes tool's list to LLM by the config parameter.

