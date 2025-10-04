# @mst/template

A CLI tool for Office 365 authentication and project template generation.

## Features

- 🔐 **Secure Authentication**: OAuth 2.0 with PKCE for Office 365
- 🏗️ **Template Generation**: Download and extract project templates
- 🔄 **Token Management**: Automatic token refresh and secure storage
- 📦 **Easy Installation**: Available via npx

## Installation

```bash
npx @mst/template <command>
```

## Usage

### Login
Authenticate with Office 365:
```bash
npx @mst/template login
```

### Generate Template
Download and extract a project template:
```bash
npx @mst/template generate <template-name>
```

### Logout
Remove stored authentication tokens:
```bash
npx @mst/template logout
```

### Server
Start the template API server:
```bash
npx @mst/template server
npx @mst/template server --port 3001
```

### Help
Display help information:
```bash
npx @mst/template help
```

## Configuration

The tool requires the following environment variables:

### Required
- `MST_CLIENT_ID`: Office 365 application client ID
- `MST_TENANT_ID`: Office 365 tenant ID

### Optional
- `MST_API_URL`: API endpoint for template downloads (default: http://localhost:3001/api/templates)

### Quick Setup
```bash
export MST_CLIENT_ID="your-client-id"
export MST_TENANT_ID="your-tenant-id"
export MST_API_URL="https://your-api.com/api/templates"  # optional
```

For detailed setup instructions, see [CONFIGURATION.md](CONFIGURATION.md).

## Token Storage

Authentication tokens are stored securely in:
- **Linux/macOS**: `~/.mst-template/tokens.json`
- **Windows**: `C:\Users\user\.mst-template\tokens.json`

Tokens are automatically refreshed when expired.

## API Server

The package includes an Express.js API server for template management:

### Endpoints
- `GET /health` - Health check
- `GET /callback` - OAuth callback (no authentication required)
- `GET /api/templates` - List available templates
- `GET /api/templates/:name` - Download template (requires Bearer token)
- `POST /api/templates/:name` - Upload template (requires Bearer token)

### Authentication
All API endpoints (except health check and callback) require a valid Bearer token from Office 365 authentication.

### Example Usage
```bash
# Start the server
npx @mst/template server

# Test with curl
curl -H "Authorization: Bearer YOUR_TOKEN" http://localhost:3001/api/templates
```

## Development

### Prerequisites
- Node.js 16+
- npm or yarn

### Setup
```bash
git clone <repository>
cd mst-template
npm install
npm run build
```

### Scripts
- `npm run build`: Compile TypeScript to JavaScript
- `npm run dev`: Run in development mode
- `npm start`: Run compiled version
- `npm run server`: Start API server
- `npm run server:dev`: Start API server in development mode
- `npm run test:all`: Run all tests including API tests

## Security

- Tokens are stored with restricted file permissions (600)
- OAuth 2.0 with PKCE for secure authentication
- Automatic token refresh to minimize exposure
- Secure token deletion on logout

## License

ISC
