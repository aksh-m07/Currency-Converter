# AI Currency Converter with CrewAI

A smart currency conversion tool built using CrewAI that converts between different currencies using real-time exchange rates.

## Features

- 🚀 **Real-time exchange rates** from Exchange Rate API
- 🤖 **AI-powered agents** using CrewAI framework
- 💱 **Multi-currency support** for global currencies
- 🔒 **Secure API key management** using environment variables
- 📊 **Detailed conversion results** with financial insights

## Prerequisites

- Python 3.8+
- Exchange Rate API key (free)
- OpenAI API key (for AI agents)

## Installation

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd AI_Agents
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables:**
   ```bash
   # Copy the template
   cp env_template.txt .env
   
   # Edit .env with your actual API keys
   nano .env
   ```

4. **Add your API keys to `.env`:**
   ```bash
   EXCHANGE_RATE_API_KEY=your_exchange_rate_api_key_here
   OPENAI_API_KEY=your_openai_api_key_here
   ```

## Usage

### Basic Usage

```python
from currency_converter import CurrencyConverterTool

# Create converter instance
converter = CurrencyConverterTool()

# Convert currency
result = converter._run(100, "USD", "EUR")
print(result)
# Output: "100 USD is equivalent to 85.50 EUR"
```

### Using CrewAI Agents

```python
from crewai import Agent, Task, Crew
from currency_converter import CurrencyConverterTool

# Create agent
currency_analyst = Agent(
    role="Currency Analyst",
    goal="Convert currencies accurately",
    tools=[CurrencyConverterTool()],
    verbose=True
)

# Create task
task = Task(
    description="Convert 100 USD to EUR",
    agent=currency_analyst
)

# Create and run crew
crew = Crew(agents=[currency_analyst], tasks=[task])
result = crew.kickoff()
```

## Project Structure

```
AI_Agents/
├── currency_converter.py      # Main currency conversion tool
├── notebook.ipynb            # Jupyter notebook with examples
├── requirements.txt           # Python dependencies
├── .env                      # Environment variables (create this)
├── .gitignore               # Git ignore rules
└── README.md                # This file
```

## API Keys

### Exchange Rate API
- **Get free API key**: [Exchange Rate API](https://www.exchangerate-api.com/)
- **Rate limits**: Usually generous for free tier
- **Coverage**: 170+ currencies worldwide

### OpenAI API
- **Get API key**: [OpenAI Platform](https://platform.openai.com/api-keys)
- **Cost**: Very cheap (~$0.002 per 1K tokens)
- **Free tier**: $5 credit when you sign up

## Configuration

The tool automatically reads API keys from environment variables:
- `EXCHANGE_RATE_API_KEY`: Your exchange rate API key
- `OPENAI_API_KEY`: Your OpenAI API key for AI agents

## Error Handling

The tool includes comprehensive error handling for:
- Missing API keys
- Invalid currency codes
- API rate limits
- Network connectivity issues

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## License

This project is open source and available under the [MIT License](LICENSE).

## Support

If you encounter any issues:
1. Check that all API keys are set correctly
2. Verify internet connectivity
3. Check API rate limits
4. Open an issue on GitHub

## Example Output

```
Agent: Starting currency conversion task...
Agent: Analyzing the goal: Convert 100 USD to EUR
Agent: Using CurrencyConverterTool with parameters: amount=100, from_currency=USD, to_currency=EUR
Agent: Tool returned: 100 USD is equivalent to 85.50 EUR
Agent: Task completed successfully!
```

---

**Happy converting! 💱✨**
