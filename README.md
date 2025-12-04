Gemini 文件操作智能代理
这是一个基于 Google Gemini LLM 的智能代理示例，提供文件读写和目录浏览功能。代理通过循环方式运行，接收用户输入，分析请求并调用相应工具，最后将工具执行结果整合到 LLM 响应中返回给用户。

功能特点
智能文件操作：读取文件内容、写入文件、列出目录结构
工具调用机制：LLM 识别用户意图并选择合适的工具执行
上下文保持：在对话过程中保持上下文信息
循环交互模式：持续接收用户输入并提供响应
配置化工具列表：启动时通过配置参数向 LLM 传递可用工具信息
工作原理
初始化阶段：

创建 Gemini LLM 客户端连接
定义并注册可用工具（读取、写入、列出文件）
将工具列表通过配置参数传递给 LLM
交互循环：

接收用户输入
将输入发送给 LLM 进行分析
LLM 识别用户意图并返回相应的工具调用指令
代理执行工具并获取结果
将工具执行结果整合后发送给 LLM
LLM 生成最终响应返回给用户
循环继续等待下一个用户输入
工具调用流程：

当用户请求列出目录内容时，LLM 返回 "list_files" 工具名称
代理执行该工具获取目录内容
将目录内容作为上下文传递给 LLM
LLM 生成包含目录信息的自然语言响应
快速开始
前提条件
Python 3.8 或更高版本
Google API 密钥（设置为环境变量 GOOGLE_API_KEY）
安装依赖：pip install google-generativeai python-dotenv
安装与运行
克隆仓库：

git clone <repository-url>
cd <repository-directory>
创建并配置 .env 文件：

GOOGLE_API_KEY=your_api_key_here
运行代理：

python agent.py
使用示例
用户: 请列出当前目录下的文件
代理: 正在获取当前目录内容...
代理: 当前目录包含以下文件和文件夹：
- README.md
- agent.py
- requirements.txt
- .env

用户: 请读取 README.md 文件的内容
代理: 正在读取 README.md 文件...
代理: README.md 文件内容如下：
# Gemini 文件操作智能代理
这是一个基于 Google Gemini LLM 的智能代理示例...

用户: 在当前目录创建一个名为 example.txt 的文件，内容为 "Hello, Gemini!"
代理: 正在创建 example.txt 文件...
代理: 文件已成功创建，内容为 "Hello, Gemini!"
工具说明
1. list_files
功能：列出指定目录下的所有文件和文件夹
参数：
dir：要列出的目录路径（默认为当前目录）
返回：目录内容列表
2. read_file
功能：读取指定文件的内容
参数：
file_path：文件路径
返回：文件内容文本
3. write_file
功能：创建或覆盖文件并写入内容
参数：
file_path：文件路径
content：要写入的内容
返回：操作结果状态
配置选项
代理支持以下配置选项：

model：使用的 Gemini 模型名称（默认为 "gemini-1.5-flash"）
temperature：生成内容的随机性（0.0-1.0，默认为 0.7）
max_output_tokens：最大输出令牌数（默认为 1000）
tools：可用工具列表（可自定义扩展）
扩展开发
要添加新工具，只需：

创建工具函数，接收参数并返回结果
在工具注册列表中添加工具描述和函数引用
确保工具描述清晰说明功能和参数，以便 LLM 正确调用
许可证
MIT License

贡献
欢迎提交 Issue 和 Pull Request 来改进这个项目！
