# Shareable MTPro2 Unicode-MATH converter

For ordinary users, share and double-click
`dist/MTPro2-Unicode-Math-Converter.exe`. It is a one-file GUI application and
does not depend on the recipient's `.py` file association or Python
installation. `dist/mtpro2_unicode_converter.py` is the equivalent inspectable
source distribution for advanced users.

Both files embed the conversion and audit programs but intentionally contain no
MTPro2 font, metric, outline, or declaration data. Each recipient must supply
their own licensed MTPro2 installation directory and a FontForge
`ffpython.exe`.

Run it by double-clicking the file, or use:

```powershell
MTPro2-Unicode-Math-Converter.exe
```

The graphical interface asks for:

1. The recipient's MTPro2 directory, containing `mtpro2_full.tex`, `.pfb`, and
   `.tfm` files.
2. An empty output directory, never named `build`.
3. FontForge's `ffpython.exe`.
4. Optionally, a template font directory to receive the generated runtime
   files.

The output contains three OpenType-MATH fonts, Cloverbook compatibility style
files, mappings and metrics, a command manifest, a complete command log, and
`mtpro2-converter-verification.json`. A result is accepted only when the
report status is `PASS`; it checks every manifest hash, all in-pipeline audit
reports, and that every generated OTF parses with an OpenType `MATH` table.

Before sharing, verify the program itself without using MTPro2:

```powershell
MTPro2-Unicode-Math-Converter.exe --self-check
```

For an actual conversion, use the **Check inputs** button first, then
**Convert and verify**. The wrapper does not claim visual equivalence unless a
separate legacy-vs-Unicode regression fixture set is also run; the scope is
recorded verbatim in the generated verification report.
