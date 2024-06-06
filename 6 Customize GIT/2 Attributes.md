Sure, here's a summarized cheat sheet based on the information provided about Git Attributes:

### Git Attributes Cheat Sheet

#### Binary Files:
- **Identifying Binary Files:**
  - Use `.gitattributes` to specify binary files.
  - Example: `*.pbxproj binary`

- **Diffing Binary Files:**
  - Configure custom diffing for binary files.
  - Example: `*.docx diff=word`

#### Keyword Expansion:
- **Identify Files for Keyword Expansion:**
  - Use `.gitattributes` to set files for keyword expansion.
  - Example: `*.txt ident`

- **Customize Keyword Expansion:**
  - Use "smudge" and "clean" filters for custom expansions.
  - Example: `*.c filter=indent`

#### Exporting Your Repository:
- **Ignoring Files in Export:**
  - Use `export-ignore` to exclude files from export.
  - Example: `test/ export-ignore`

- **Substituting Metadata on Export:**
  - Use `export-subst` to inject metadata into exported files.
  - Example: `LAST_COMMIT export-subst`

#### Merge Strategies:
- **Custom Merge Strategy:**
  - Specify merge strategies for specific files.
  - Example: `database.xml merge=ours`