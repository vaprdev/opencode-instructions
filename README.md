# opencode instructions

Personal opencode instruction files I use to bias agents toward simpler, more careful software engineering.

These are not official opencode defaults. They are personal preferences intended to be copied, modified, or ignored.

The files are inspired by public ideas from Andrej Karpathy and Rich Hickey, but are not affiliated with, endorsed by, or authored by either of them.

## Usage

Add the files you want to your opencode config:

```json
{
  "instructions": [
    "/path/to/instructions/llm-coding-guidelines.md",
    "/path/to/instructions/simplicity-principles.md",
    "/path/to/instructions/beginner-friendly-explanations.md"
  ]
}
```

Instructions are loaded into every session. Keep them short and broadly applicable.

## Files

- `instructions/llm-coding-guidelines.md`: general behavior for careful LLM-assisted coding.
- `instructions/simplicity-principles.md`: simplicity-focused design principles for software work.
- `instructions/beginner-friendly-explanations.md`: brief beginner-friendly context when explaining concepts.

## License

MIT
