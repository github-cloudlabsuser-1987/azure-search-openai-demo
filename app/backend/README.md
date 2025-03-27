# Backend Application Documentation

## Overview
This is the backend component of the Azure Search OpenAI Demo application. It provides a REST API for document search, question answering, and chat functionality using Azure OpenAI and Azure AI Search services.

## Components

### Main Components
- `main.py` - Application entry point that creates and runs the Quart web server
- `approaches/` - Different implementation approaches for search and Q&A
- `core/` - Core functionality and authentication helpers
- `text/` - Text processing utilities

### Key Classes

#### Approach Class
Base abstract class that provides core functionality for:
- Document search using Azure AI Search
- Text embedding generation with Azure OpenAI
- Image embedding with Azure Computer Vision
- Authentication and filtering

#### Document Class
Data class representing search results with:
- Document content and metadata
- Text and image embeddings
- Search scores and rankings
- Source citations and captions

## Requirements

Main dependencies (see requirements.txt for complete list):
- aiohttp - For async HTTP requests
- azure-search-documents - Azure AI Search client
- azure-storage-blob - Azure Blob Storage client
- openai - OpenAI API client 
- quart - Async web framework
- azure-identity - Azure authentication
- azure-keyvault-secrets - Key Vault integration
- azure-monitor-opentelemetry - Telemetry

## Configuration

The application requires the following environment variables:
- `AZURE_SEARCH_SERVICE` - Azure AI Search service endpoint
- `AZURE_SEARCH_INDEX` - Name of the search index
- `AZURE_OPENAI_SERVICE` - Azure OpenAI service endpoint
- `AZURE_OPENAI_DEPLOYMENT` - Model deployment name
- `AZURE_OPENAI_API_VERSION` - OpenAI API version to use

Optional configuration:
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT` - Embedding model deployment
- `AZURE_VISION_ENDPOINT` - Computer Vision endpoint for image processing
- `AZURE_USE_AUTHENTICATION` - Enable/disable authentication

## API Endpoints

The backend exposes the following main endpoints:

### /api/approach/chat
Chat endpoint that provides:
- Contextual conversation with documents
- Document retrieval and citation
- Support for both text and semantic search

### /api/approach/qa 
Question-answering endpoint that:
- Answers questions using indexed documents
- Returns relevant document citations
- Supports different search approaches

## Development

To run locally:
1. Install dependencies: `pip install -r requirements.txt`
2. Set required environment variables
3. Run the development server: `python -m quart run`

## Monitoring

The application includes:
- Application Insights integration
- OpenTelemetry tracing
- Performance monitoring for search and embedding operations

## Security

Security features include:
- Azure AD authentication (optional)
- Request filtering and validation
- Secure secret management with Key Vault

## Contributing

When adding new features:
1. Add appropriate documentation
2. Include docstrings for new functions/classes
3. Add telemetry for monitoring
4. Follow existing code style and patterns

## License

This project is licensed under the MIT License - see the LICENSE file for details.
