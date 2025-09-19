# TrendRadar - Development Guidelines

## Build/Test/Lint Commands

### Main Application
```bash
# Run the main crawler
python main.py

# Install dependencies
pip install -r requirements.txt
```

### Docker Commands
```bash
# Build and run with Docker
docker-compose up -d

# View logs
docker logs -f trend-radar

# Manual execution inside container
docker exec -it trend-radar python manage.py run
```

### Testing
```bash
# Run single test (if tests exist)
python -m pytest tests/test_specific_module.py -v

# Run all tests
python -m pytest
```

## Code Style Guidelines

### Python Style
- **Line length**: 120 characters maximum
- **Imports**: Group standard library, third-party, and local imports
- **Type hints**: Use `typing` module for all function signatures
- **Naming**: 
  - Functions: `snake_case`
  - Variables: `snake_case` 
  - Classes: `PascalCase`
  - Constants: `UPPER_SNAKE_CASE`

### Error Handling
- Use specific exceptions instead of generic `Exception`
- Always include descriptive error messages
- Use try-except blocks for external API calls and file operations

### Code Structure
- Keep functions small and focused (single responsibility)
- Use docstrings for all public functions
- Separate configuration, data processing, and business logic

### File Organization
- `main.py`: Main application entry point
- `config/`: Configuration files (YAML, frequency words)
- `docker/`: Docker-related files
- `output/`: Generated reports and data
- `.github/workflows/`: CI/CD pipelines

### Dependencies
- requests==2.32.4 (HTTP requests)
- pytz==2025.2 (Timezone handling)
- PyYAML==6.0.2 (Configuration parsing)

### Configuration
- Use `config/config.yaml` for all application settings
- Use `config/frequency_words.txt` for keyword filtering
- Never commit sensitive webhooks to version control

### Logging
- Use print statements for user-facing messages
- Include timestamps and context for debugging
- Log both Chinese and English messages for international users