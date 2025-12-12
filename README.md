<img width="128" height="128" alt="icon-128" src="https://github.com/user-attachments/assets/f01fe201-63c0-4559-abfc-1f2643afa6f4" />

# CDoc Pseudocode Syntax

C syntax highlighting for `.cdoc` files designed for reverse engineering workflows. Write C-style pseudocode without error analysis, IntelliSense interference, or compiler warnings.

## Purpose

When reverse engineering binaries, you often need to document functions and structures in C-like pseudocode. The standard C/C++ extension shows errors for missing headers, undefined types, and incomplete code. CDoc provides clean C syntax highlighting without the noise.

## Features

### Core Highlighting
- Complete C syntax highlighting (keywords, operators, strings, numbers, comments)
- Bracket matching and auto-closing pairs
- Smart indentation and formatting
- No error squiggles or IntelliSense

### Reverse Engineering Focused

**Calling Conventions & Microsoft Attributes**
- `__fastcall`, `__stdcall`, `__cdecl`, `__thiscall`, `__vectorcall`
- `__declspec`, `WINAPI`, `CALLBACK`, `NTAPI`
- `__forceinline`, `__inline`, `__noinline`

**Disassembler Name Recognition**
- IDA/Ghidra function names: `sub_140001000`, `nullsub_5`, `j_sub_140002000`
- Labels: `loc_140001234`, `locret_140001500`
- Data references: `dword_140003000`, `qword_140004000`, `byte_140005000`
- Unknowns: `unk_140006000`, `off_140007000`

**Extended Type Support**
- Windows API types: `DWORD`, `HANDLE`, `NTSTATUS`, `BOOL`, `PVOID`
- Standard integer types: `uint32_t`, `size_t`, `intptr_t`
- NT/Kernel types: `UNICODE_STRING`, `OBJECT_ATTRIBUTES`, `IO_STATUS_BLOCK`
- Kernel structures: `PEPROCESS`, `PETHREAD`, `PDRIVER_OBJECT`, `PIRP`
- Security types: `ACCESS_MASK`, `SECURITY_DESCRIPTOR`, `TOKEN_PRIVILEGES`
- Common status codes: `STATUS_SUCCESS`, `STATUS_ACCESS_DENIED`, etc.

**Special Highlighting**
- Memory addresses: `0x140001000` (6-16 hex digits)
- TODO/FIXME/NOTE/RESEARCH comments are highlighted
- Function call recognition

### Code Snippets

Type these prefixes and press Tab:
- `func` - Function skeleton
- `struct` - Structure definition
- `todo` - TODO comment
- `ifstatus` - NT status check
- `ifnull` - NULL check
- `unistr` - UNICODE_STRING initialization
- `virtmem` - Virtual memory pattern
- `apihash` - API hash resolution
- `obfcall` - Obfuscated call pattern

## Usage

Simply create files with the `.cdoc` extension and start documentation your reverse engineering process in pseudocode.

## Installation

### From Source
1. Copy to VSCode extensions directory:
   - Windows: `%USERPROFILE%\.vscode\extensions\cdoc-syntax`
   - macOS/Linux: `~/.vscode/extensions/cdoc-syntax`
2. Restart VSCode

### From VSIX
1. Download the `.vsix` file
2. Run: `code --install-extension cdoc-syntax-1.0.0.vsix`

## Customization

### Adding Custom Types
Edit `syntaxes/cdoc.tmLanguage.json` and add your types to the appropriate pattern. For example, to add custom game engine types:

```json
{
    "name": "storage.type.custom.cdoc",
    "match": "\\b(CGameObject|CPlayer|CEntity)\\b"
}
```

### Custom Snippets
Add your own snippets to `snippets/cdoc.json` following the VSCode snippet format.

## License

MIT
