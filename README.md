# 𝕱𝖆𝕟𝕔𝖎𝑓ʸ𝗽𝗒

Are you tired of boring Python code?
Or do you want to make a real impression with your next PR?
Look no further!
𝔽𝚊𝘯ⅽⅈ𝙛ʸₚ𝐲 will transform any plain and boring Python code into a feast for the eyes.

```python
pipx run fancifypy code "print(range(5))" --seed 42
```

```raw
ｐᵣⁱⁿｔ ( ᵣ𝙖𝕟ᵍ𝐞 ( 5 ) )
```

Alternatively, you can fancify files directly

```python
pipx run fancifypy path script.py
```

and defancified files (if you for some reason want boring files again)

```python
pipx run fancifypy boring script.py
```

Note that 𝖥𝑎𝐧𝘤𝒊𝔣𝙮𝘱𝐲 leaves somewhat odd whitespaces, so we recommend using [Ruff](https://docs.astral.sh/ruff/) or [Black](https://github.com/psf/black) afterwards to format the code.

## Is this safe?

ℱ𝔞𝑛𝚌𝔦𝒻𝓎𝐩𝒚 checks that the abstract syntax tree doesn't change after fancifying, so this is 100% safe (for CPython).
This means that any code that imported your code before fancifying will also work with it after fancifying with no modifications.

## How does this work?

When CPython looks up identifiers, it first [normalizes the code using "NFKC" normalization](https://docs.python.org/3.6/reference/lexical_analysis.html#identifiers).
This program detects identifiers in a Python file and replaces all character with a different character that normalizes to it.
So for Python, there is no change in the files.
