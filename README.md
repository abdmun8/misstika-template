# @misstika/template

A CLI project generation tool for MST Developer.

## Features

- 🔐 **Secure Authentication**: OAuth 2.0 with PKCE for Office 365
- 🏗️ **Template Generation**: Download and extract project templates
- 🔄 **Token Management**: Automatic token refresh and secure storage
- 📦 **Easy Installation**: Available via npx

## Installation

```bash
npx @misstika/template <command>
```

## Usage

### Login
Authenticate with Office 365:
```bash
npx @misstika/template login
```

### Generate Template
Download and extract a project template:
```bash
npx @misstika/template generate <template-name>
```

### Logout
Remove stored authentication tokens:
```bash
npx @misstika/template logout
```

### Help
Display help information:
```bash
npx @misstika/template help
```

## Token Storage

Authentication tokens are stored securely in:
- **Linux/macOS**: `~/.misstika-template/tokens.json`
- **Windows**: `C:\Users\user\.misstika-template\tokens.json`

Tokens are automatically refreshed when expired.

## Security

- Tokens are stored with restricted file permissions (600)
- OAuth 2.0 with PKCE for secure authentication
- Automatic token refresh to minimize exposure
- Secure token deletion on logout

## License

ISC
