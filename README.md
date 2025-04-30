# Log Analyzer Tool

![License: Apache-2.0](https://img.shields.io/badge/License-Apache%202.0-green.svg)
![Shell Script](https://img.shields.io/badge/Shell_Script-121011?style=flat&logo=gnu-bash&logoColor=white)

## OVERVIEW

**Log Analyzer** is a command-line tool designed to extract meaningful insights from web server log files. The tool provides rich analytics with colorized output, filtering capabilities, and statistics about your server traffic.

Perfect for:
- DevOps engineers troubleshooting server issues
- Web admins tracking usage patterns and performance
- Developers debugging application behavior

## FEATURES

- **Colorized Output**: Clear, readable output with color-coded sections
- **Analytics**: Analyze IPs, paths, status codes, user agents, and HTTP methods
- **Filtering**: Filter logs by IP, path or status code
- **Statistics**: View percentage breakdowns and traffic summaries
- **Zero Dependencies**: Works with standard Unix tools available on any system
- **Customizable Output**: Control verbosity and focus on specific sections

## INSTALLATION

```bash
# Clone this repository
git clone https://github.com/elidholm/log-analyzer-tool.git

# Navigate to the project directory
cd log-analyzer

# Make the script executable
chmod +x src/log-analyzer

# Optional: Move to a directory in your PATH for system-wide access
sudo cp src/log-analyzer /usr/local/bin/log-analyzer
```

## USAGE

### Basic Usage

```bash
log-analyzer access.log
```

### Advanced Options

```
Usage: log-analyzer [OPTIONS] <log-file>

Options:
  -h, --help     Display help message and exit
  -v, --verbose  Display more detailed output
  -n <number>    Show top N results (default: 5)
  -o <section>   Only show specific section (ip, path, status, agent)
  -i <ip>        Filter by specific IP address
  -p <path>      Filter by specific path
  -s <status>    Filter by HTTP status code
  --no-summary   Skip the summary section
```

### Examples

Display top 5 results from each category:
```bash
log-analyzer /var/log/nginx/access.log
```

Show top 10 results with additional details:
```bash
log-analyzer -v -n 10 /var/log/nginx/access.log
```

Only analyze traffic from a specific IP:
```bash
log-analyzer -i 192.168.1.100 /var/log/nginx/access.log
```

Find all 404 errors:
```bash
log-analyzer -s 404 /var/log/nginx/access.log
```
## EXAMPLE OUTPUT

```
Log Analyzer Report
Generated on: 2025-04-30 13:23:00
Analyzing log file: /var/log/nginx/access.log

==== Top 5 IP Addresses ====
192.168.1.100 - 4 requests
192.168.1.101 - 2 requests
192.168.1.102 - 2 requests
192.168.1.103 - 1 requests
192.168.1.104 - 1 requests

==== Top 5 Request Paths ====
/api/v1/users - 3 requests
/api/v1/products - 3 requests
/api/v1/orders - 1 requests
/api/v1/health - 1 requests
/api/v1/products/featured - 1 requests

==== Top 5 HTTP Status Codes ====
200 - 6 requests
401 - 1 requests
404 - 1 requests
500 - 1 requests
204 - 1 requests

==== Top 5 User Agents ====
Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 - 4 requests
Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 - 2 requests
curl/7.68.0 - 2 requests
python-requests/2.25.1 - 1 requests
Googlebot/2.1 (+http://www.google.com/bot.html) - 1 requests

==== HTTP Methods ====
GET - 8 requests
POST - 1 requests
DELETE - 1 requests

==== Request Summary ====
Total Requests: 10

Successful Responses (2xx): 7 (70.00%)
Redirects (3xx): 0 (0.00%)
Client Errors (4xx): 2 (20.00%)
Server Errors (5xx): 1 (10.00%)

Analysis completed at: 2025-04-30 13:23:00
```

## COMPATIBLE LOG FORMATS

This tool works with standard log formats:

- NGINX access logs
- Apache common/combined logs
- Most web server logs with similar structure

Example log entry format:
```
192.168.1.1 - - [29/Apr/2025:12:34:56 +0000] "GET /api/v1/users HTTP/1.1" 200 1234 "https://example.com" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36"
```

## CI/CD Pipeline

This project uses GitHub Actions for continuous integration and deployment:

- **Automated Testing**: Tests the script with various options and settings
- **ShellCheck**: Ensures code quality and best practices
- **YamlLint**: Validates YAML files for configuration
- **Automated Releases**: Generates releases with changelogs when version tags are pushed

## CONTRIBUTING

Contributions are welcome! To contribute:

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/amazing-feature`
3. Commit your changes: `git commit -am 'Add some amazing feature'`
4. Push to the branch: `git push origin feature/amazing-feature`
5. Open a pull request

Please make sure to update tests as appropriate and adhere to the code style.

## LICENSE

This project is licensed under the Apache-2.0 License - see the [LICENSE](LICENSE) file for details.

## LEARN MORE

This project is part of the DevOps roadmap. To learn more about server administration, log analysis, and shell scripting, visit: <https://roadmap.sh/projects/nginx-log-analyser>
