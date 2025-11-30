This project follows the authenticity.txt protocol
[![](https://img.shields.io/badge/authenticity.txt-enabled-2563eb)]()

# authenticity.txt — Minimal Public Authenticity Protocol

authenticity.txt is a simple, text-only file placed at the root of any website or project to declare how published content was created: by humans, by AI systems, or by a mix of both. All declarations must be objectively verifiable by anyone. The protocol is technology-neutral, organization-neutral, identity-neutral, and fully open.

## Specification (v0.1)

The authenticity.txt file must follow the seven universal rules defined by the protocol:

### 1. File Location
A plain UTF-8 text file named authenticity.txt must exist at the root of the domain or project. It must be publicly accessible without cookies, JavaScript, authentication, or redirects, and contain one declaration per line using the format key: value.

### 2. Origin Declaration
The file must declare how the covered content was created using one of the following values: origin: human, origin: ai, or origin: mixed.

### 3. AI Involvement
If AI contributed, the file must declare the systems or models used and their roles (for example: ai-system: <model family>, ai-role: draft, assist, translate, summarize, generate-media).

### 4. Human Involvement
If humans contributed, the file must declare their functional roles without using personal identifiers (for example: human-role: author, editor, reviewer).

### 5. Visibility of Origin
The file must declare whether human-origin or AI-origin notices are visible to users (for example: ai-origin-labels: visible, partial, or none).

### 6. Authenticity Updates
The file must declare how authenticity information is updated when content changes (for example: authenticity-updates: on-change, periodic, or versioned).

### 7. Proof of Integrity
The file must include a sha256: line containing the SHA-256 hash of the file itself (computed over the file content excluding the sha256: line).  
Example: sha256: <sha256_value>

## Example authenticity.txt file

origin: mixed  
ai-system: large-language-model  
ai-role: draft, translation  
human-role: editor, reviewer  
ai-origin-labels: visible  
authenticity-updates: on-change  
sha256: (SHA-256 of this file)

## How to Verify

1. Download the authenticity.txt file from the root of the domain.  
2. Remove the sha256: line.  
3. Compute the SHA-256 hash of the remaining content.  
4. Compare the computed value with the sha256: value published in the file.  
5. Independently verify each declaration (origin, ai-system, ai-role, human-role, visibility, updates) against publicly observable information.  
6. If any declaration cannot be verified, the implementation is non-compliant.

## SHA-256 Verification Tools

Local tools: sha256sum, shasum -a 256, Get-FileHash  
Online tools: https://emn178.github.io/online-tools/sha256_checksum.html, https://hash.expert, https://www.virustotal.com/gui/file-analysis  
Automated verification (optional): https://api.timeproofs.io/api/verify?hash=<SHA256>

## Related Protocols

The authenticity.txt protocol can be used alongside other independent, root-level transparency standards:

- integrity.txt — public integrity and tracking declarations  
- rights.txt — digital rights and usage declarations  
- explainable-ia.txt — AI explainability and model transparency declarations

These standards are independent and can be implemented separately or together.

## License

This protocol is released under the MIT License.
