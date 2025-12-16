# NMAP to Metasploit Script

## Project Description
This Python tool takes Nmap scan results in XML format and generates a Metasploit resource script (.rc) to automate safe enumeration of detected services. It focuses on reconnaissance (e.g., banner grabs, anonymous FTP checks) without destructive actions.

Built as part of the Azerbaijan Cybersecurity Center project. Key features:
- Parses Nmap XML for services/ports.
- Maps services (e.g., HTTP, FTP, SMB, SSH, SNMP) to safe Metasploit auxiliary modules.
- Generates .rc scripts with workspace setup, db_import, and module runs.
- Dry-run mode for previewing actions.
- Optional LLM integration (ChatGPT/Gemini) for module suggestions.

## Dependencies
- Python 3.x
- Install via: `pip install -r requirements.txt`
  (Likely includes libraries like `xml.etree.ElementTree` for parsing, `pyyaml` for mappings, and optionally `openai` for LLM.)

## Usage Instructions
1. Run an Nmap scan: `nmap -oX scan.xml [target]`
2. Run the tool: `python main.py --input scan.xml --output script.rc`
   - Optional flags: `--dry-run` (list modules without writing file), `--threads 5` (for parallel runs).
3. Load in Metasploit: `msfconsole -r script.rc`

### Example
Input: Nmap XML with open HTTP port.
Output: .rc script with `auxiliary/scanner/http/http_version` module.

## Safety Notes
This tool is for educational/pentesting purposes only. It avoids brute-force or exploitative modules unless specified. Always get permission before scanning networks.

## Testing
Includes unit tests for XML parsing and .rc generation. Example: `python -m unittest tests.py`

For more details, see the [project spec PDF](project-spec.pdf).
