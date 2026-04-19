# stdio.h Complete Reference

This file provides a near-complete reference for `stdio.h`.
Each function includes:

* Syntax
* Description
* Return value
* Warnings and pitfalls
* Example where useful

---

# Formatted Output

## printf

```c
int printf(const char *format, ...);
```

Description:
Writes formatted output to stdout.

Return:
Number of characters printed, negative on error.

> [!WARNING]
> Incorrect format specifiers cause undefined behavior.

Example:

```c
printf("%d\n", 42);
```

---

## fprintf

```c
int fprintf(FILE *stream, const char *format, ...);
```

Writes formatted output to a stream.

---

## sprintf

```c
int sprintf(char *str, const char *format, ...);
```

Writes formatted output to buffer.

> [!WARNING]
> No bounds checking. High risk of buffer overflow.

---

## snprintf

```c
int snprintf(char *str, size_t size, const char *format, ...);
```

Safe version of sprintf.

> [!NOTE]
> Always prefer this over sprintf.

---

# Formatted Input

## scanf

```c
int scanf(const char *format, ...);
```

Reads formatted input from stdin.

Return:
Number of assigned items.

> [!WARNING]
> Passing wrong pointer types leads to undefined behavior.

---

## fscanf

```c
int fscanf(FILE *stream, const char *format, ...);
```

Reads formatted input from stream.

---

## sscanf

```c
int sscanf(const char *str, const char *format, ...);
```

Reads formatted data from string.

---

# Character I/O

## getchar

```c
int getchar(void);
```

Reads a character from stdin.

Return:
Character or EOF.

---

## putchar

```c
int putchar(int c);
```

Writes a character to stdout.

---

## getc

```c
int getc(FILE *stream);
```

Reads character from stream.

> [!NOTE]
> May be implemented as macro.

---

## putc

```c
int putc(int c, FILE *stream);
```

Writes character to stream.

---

## ungetc

```c
int ungetc(int c, FILE *stream);
```

Pushes character back onto stream.

> [!WARNING]
> Only one character guaranteed.

---

# String I/O

## fgets

```c
char *fgets(char *s, int n, FILE *stream);
```

Reads line safely.

> [!NOTE]
> Includes newline if present.

---

## fputs

```c
int fputs(const char *s, FILE *stream);
```

Writes string to stream.

---

## gets (removed)

```c
char *gets(char *s);
```

> [!WARNING]
> Removed from C11. Causes buffer overflow. Never use.

---

# File Operations

## fopen

```c
FILE *fopen(const char *filename, const char *mode);
```

Opens file.

Return:
FILE pointer or NULL.

---

## freopen

```c
FILE *freopen(const char *filename, const char *mode, FILE *stream);
```

Reopens stream.

---

## fclose

```c
int fclose(FILE *stream);
```

Closes file.

---

## fflush

```c
int fflush(FILE *stream);
```

Flushes output buffer.

> [!NOTE]
> fflush(NULL) flushes all output streams.

---

# Binary I/O

## fread

```c
size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream);
```

Reads binary data.

Return:
Items read.

---

## fwrite

```c
size_t fwrite(const void *ptr, size_t size, size_t nmemb, FILE *stream);
```

Writes binary data.

---

# File Positioning

## fseek

```c
int fseek(FILE *stream, long offset, int whence);
```

Moves file position.

---

## ftell

```c
long ftell(FILE *stream);
```

Gets current position.

---

## rewind

```c
void rewind(FILE *stream);
```

Resets position to start.

---

## fgetpos

```c
int fgetpos(FILE *stream, fpos_t *pos);
```

Stores position.

---

## fsetpos

```c
int fsetpos(FILE *stream, const fpos_t *pos);
```

Restores position.

---

# Error Handling

## feof

```c
int feof(FILE *stream);
```

Checks EOF indicator.

---

## ferror

```c
int ferror(FILE *stream);
```

Checks error indicator.

---

## clearerr

```c
void clearerr(FILE *stream);
```

Clears error flags.

---

## perror

```c
void perror(const char *s);
```

Prints error message.

---

# Temporary Files

## tmpfile

```c
FILE *tmpfile(void);
```

Creates temporary file.

---

## tmpnam

```c
char *tmpnam(char *s);
```

Generates temp filename.

> [!WARNING]
> Not safe for concurrent use.

---

# Buffering

## setbuf

```c
void setbuf(FILE *stream, char *buf);
```

Sets buffer.

---

## setvbuf

```c
int setvbuf(FILE *stream, char *buf, int mode, size_t size);
```

Controls buffering.

> [!NOTE]
> Must be called before any I/O.

---

# Constants and Types

* FILE
* EOF
* BUFSIZ
* FILENAME_MAX
* SEEK_SET, SEEK_CUR, SEEK_END

---

# Real World Pitfalls

> [!WARNING]
> Mixing buffered I/O with low-level I/O (read/write) causes undefined behavior.

> [!WARNING]
> Not checking fopen return value leads to crashes.

> [!WARNING]
> Using scanf for strings without width limit causes buffer overflow.

> [!NOTE]
> Always prefer fgets + sscanf for safer input parsing.

---

# End

