# AI Multi-Source Research Agent

An intelligent research agent that leverages AI to provide comprehensive answers by simultaneously searching and analyzing results from Google, Bing, and Reddit. The agent uses LangGraph for orchestrating parallel searches and GPT-4 for intelligent analysis and synthesis.

## 🚀 Key Features

- **Multi-Source Search**: Simultaneous searching across Google, Bing, and Reddit
- **Intelligent Analysis**: GPT-4 powered analysis of search results from each source
- **Reddit Deep Dive**: Automatic selection and retrieval of relevant Reddit posts and comments
- **Synthesis Engine**: Combines insights from all sources into comprehensive answers
- **Parallel Processing**: Uses LangGraph for efficient parallel search execution
- **Interactive CLI**: Simple command-line interface for research queries

## 🏗️ Architecture

The agent uses a **LangGraph state machine** with the following workflow:

```
START → [Google Search, Bing Search, Reddit Search] (Parallel)
      ↓
      Reddit URL Analysis → Reddit Post Retrieval
      ↓
      [Google Analysis, Bing Analysis, Reddit Analysis] (Parallel)
      ↓
      Final Synthesis → END
```

## 🛠️ Technologies Used

- **LangGraph**: Workflow orchestration and state management
- **OpenAI GPT-4o**: Natural language processing and analysis
- **BrightData API**: Web scraping and data collection
- **Reddit API**: Social media content retrieval
- **Pydantic**: Data validation and structured outputs
- **Python-dotenv**: Environment configuration

## 📦 Installation

1. **Clone the repository:**
```bash
git clone https://github.com/Rnamrata/ai-search-agent.git
cd ai-search-agent
```

2. **Install dependencies:**
```bash
pip install -r requirements.txt
```

3. **Set up environment variables:**
```bash
cp .env.example .env
```

Edit `.env` with your API keys:
```env
OPENAI_API_KEY=your_openai_api_key_here
BRIGHTDATA_API_KEY=your_brightdata_api_key_here
```

## ⚙️ Configuration

### Required API Keys

1. **OpenAI API Key**: Get from [OpenAI Platform](https://platform.openai.com/)
2. **BrightData API Key**: Get from [BrightData](https://brightdata.com/)

### Dataset Configuration

The agent uses two BrightData datasets:
- `gd_lvz8ah06191smkebj4`: Reddit search dataset
- `gd_lvzdpsdlw09j6t702`: Reddit post retrieval dataset

## 🚀 Usage

### Command Line Interface

Run the interactive research agent:

```bash
python main.py
```

Example session:
```
Multi-Source Research Agent
Type 'exit' to quit

Ask me anything: What are the best practices for machine learning model deployment?

Starting parallel research process...

Launching Google, Bing, and Reddit searches...

Searching Google for: What are the best practices for machine learning model deployment?
Searching Bing for: What are the best practices for machine learning model deployment?
Searching Reddit for: What are the best practices for machine learning model deployment?

Selected URLs:
   1. https://reddit.com/r/MachineLearning/...
   2. https://reddit.com/r/MLOps/...

Analyzing Google search results...
Analyzing Bing search results...
Analyzing Reddit search results...
Combine all results together...

Final Answer:
[Comprehensive synthesized answer from all sources]
```

### Programmatic Usage

```python
from main import graph

# Define your research state
state = {
    "messages": [{"role": "user", "content": "Your question here"}],
    "user_question": "Your question here",
    "google_results": None,
    "bing_results": None,
    "reddit_results": None,
    # ... other state fields
}

# Execute the research workflow
final_state = graph.invoke(state)
answer = final_state.get("final_answer")
print(answer)
```

## 📁 Project Structure

```
ai-search-agent/
├── main.py                    # Main application with LangGraph workflow
├── prompts.py                 # AI prompt templates for different analyses
├── web_operations.py          # Search API integrations (Google, Bing, Reddit)
├── snapshot_operations.py     # BrightData snapshot management
├── requirements.txt           # Python dependencies
├── .env.example              # Environment variables template
└── README.md                 # This file
```

## 🔧 Core Components

### State Management (`main.py`)

The `State` TypedDict manages the entire research pipeline:
- User questions and search results
- Analysis outputs from each source
- Final synthesized answer

### Search Operations (`web_operations.py`)

- **`serp_search()`**: Google/Bing search via BrightData
- **`reddit_search_api()`**: Reddit post discovery
- **`reddit_post_retrieval()`**: Detailed Reddit content extraction

### AI Analysis (`prompts.py`)

Specialized prompts for different analysis types:
- **Google Analysis**: Authoritative sources and verified information
- **Bing Analysis**: Technical documentation and enterprise perspectives  
- **Reddit Analysis**: Community insights and user experiences
- **Synthesis**: Comprehensive answer generation

### Workflow Nodes

1. **Search Nodes**: Parallel execution of Google, Bing, Reddit searches
2. **Reddit Processing**: URL selection and content retrieval
3. **Analysis Nodes**: AI-powered analysis of each source
4. **Synthesis Node**: Final answer generation

## 📊 Search Capabilities

### Google Search
- Authoritative sources and official documentation
- News articles and recent developments
- Academic papers and research findings

### Bing Search  
- Microsoft ecosystem perspectives
- Technical documentation
- Enterprise and business insights

### Reddit Search
- Community discussions and user experiences
- Real-world testimonials and advice
- Alternative perspectives and debates
- Automatic selection of most relevant posts (up to 75 posts)
- Deep retrieval of comments and discussions

## 🎯 Use Cases

- **Research Questions**: Get comprehensive answers from multiple perspectives
- **Product Reviews**: Combine official info with user experiences
- **Technical Queries**: Official docs + community discussions
- **Market Research**: Formal sources + community sentiment
- **Troubleshooting**: Documentation + user-reported solutions

## 🔄 Workflow Details

1. **Parallel Search Phase**: Simultaneously queries all three sources
2. **Reddit Intelligence**: AI selects most relevant Reddit URLs for deep analysis
3. **Content Retrieval**: Fetches detailed Reddit post and comment data
4. **Parallel Analysis**: AI analyzes each source with specialized prompts
5. **Synthesis**: Combines all analyses into a coherent, comprehensive answer

## 📝 Example Output Structure

The agent provides:
- **Source Attribution**: Clear identification of information sources
- **Multiple Perspectives**: Balanced view from official and community sources
- **Conflict Resolution**: Highlights contradictory information when present
- **Community Insights**: Real user experiences and discussions
- **Authoritative Facts**: Verified information from reliable sources

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Namrata Roy** - [Rnamrata](https://github.com/Rnamrata)

## 🙏 Acknowledgments

- OpenAI for GPT-4 API
- BrightData for web scraping infrastructure
- LangGraph community for workflow orchestration
- Reddit community for valuable discussions

---

⭐ If you found this project helpful, please give it a star!