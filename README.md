This project follows the authenticity.txt protocol
[![](https://img.shields.io/badge/authenticity.txt-enabled-2563eb)]()

# authenticity.txt — Minimal Public Authenticity Protocol

authenticity.txt is a simple, text-only file placed at the root of any website or project to declare how published content was created: by humans, by AI systems, or by a mix of both. All declarations must be objectively verifiable by anyone. The protocol is technology-neutral, organization-neutral, identity-neutral, and fully open.

## Specification (v0.1)

The authenticity.txt file must follow seven universal rules defined by the protocol:

### 1. File Location
A plain UTF-8 text file named authenticity.txt must exist at the root of the domain or project. It must be accessible without cookies, without JavaScript, without authentication, and without redirects, and must use one line per declaration in the format key: value.

### 2. Origin Declaration
The file must declare how the covered content was created using one of the following values: origin: human, origin: ai, or origin: mixed.

### 3. AI Involvement
If AI contributed, the file must declare the systems or models used and their roles (for example: ai-system: <model family> and ai-role: draft, assist, translate, summarize, generate-media).

### 4. Human Involvement
If humans contributed, the file must declare their functional roles without using personal identifiers (for example: human-role: author, editor, reviewer).

### 5. Visibility of Origin
The file must declare whether AI-origin or human-origin notices are visibly presented on the site or content (for example: ai-origin-labels: visible, partial, or none).

### 6. Authenticity Updates
The file must declare how authenticity information is updated when content changes (for example: authenticity-updates: on-change, periodic, or versioned).

### 7. Proof of Integrity
The file must include a line using the sha256: key containing the SHA-256 hash of the file itself. Example: sha256: <sha256_value>

## Example authenticity.txt file

origin: mixed  
ai-system: large-language-model  
ai-role: draft, translation  
human-role: editor, reviewer  
ai-origin-labels: visible  
authenticity-updates: on-change  
sha256: (SHA-256 of this file)

## How to Verify

Anyone can verify an authenticity.txt file using any SHA-256 tool. The steps are universal:
1. Download the file from the root of the domain.
2. Compute its SHA-256 hash using any local or online tool.
3. Compare the computed value with the sha256: field. They must match exactly.
4. Independently check each declaration (origin, ai-system, human-role, visibility, updates) against publicly visible information.
5. If any declaration cannot be verified, the site is non-compliant.

## Optional Tools for SHA-256 Verification

Local tools: sha256sum, shasum -a 256, Get-FileHash  
Online tools: https://emn178.github.io/online-tools/sha256_checksum.html, https://hash.expert, https://www.virustotal.com/gui/file-analysis  
Automated verification (optional): https://api.timeproofs.io/api/verify?hash=<SHA256>

## License

This protocol is released under the MIT License.
