# codeowners-utils

> Utilities for working with CODEOWNERS files

## Install

```sh
npm install --save codeowners-utils
```

## API

From the generated `dist/codeowners-utils.d.ts` file:

```ts
/**
 * An individual entry from a CODEOWNERS file
 */
export interface CodeOwnersEntry {
	pattern: string
	owners: Array<string>
}

/**
 * Parse a CODEOWNERS file into an array of entries (will be in reverse order
 * of the file).
 */
export declare function parse(str: string): Array<CodeOwnersEntry>

/**
 * Standard locations to search for the CODEOWNERS file in priority order
 * (Note: This comes from GitHub).
 */
export declare let CODEOWNERS_PATHS: string[]

/**
 * Find the path of the CODEOWNERS file from the current working directory.
 */
export declare function findOwnersPath(cwd: string): Promise<string | null>

/**
 * Find, load, and parse the CODEOWNERS file (if it exists) from the current
 * working directory.
 */
export declare function loadOwners(
	cwd: string,
): Promise<Array<CodeOwnersEntry> | null>

/**
 * Match a filename against a glob pattern (while respecting .gitignore rules)
 */
export declare function matchPattern(filename: string, pattern: string): boolean

/**
 * Match a filename against CODEOWNERS entries to determine which (if any) it
 * matches.
 */
export declare function matchFile(
	filename: string,
	entries: Array<CodeOwnersEntry>,
): CodeOwnersEntry | null

/**
 * Given a set of files and CODEOWNERS entries, return the set of files which
 * are not matched to any CODEOWNERS entries.
 */
export declare function filterUnmatchedFiles(
	files: Array<string>,
	entries: Array<CodeOwnersEntry>,
): string[]

/**
 * Find all of the files in a git repository which are not matched by any code
 * owners using a set of CODEOWNERS entries.
 */
export declare function findUnmatchedFilesFromEntries(
	entries: Array<CodeOwnersEntry>,
	cwd: string,
): Promise<Array<string>>

/**
 * Find all of the files in a git repository which are not matched by any code
 * owners.
 */
export declare function findUnmatchedFiles(
	cwd: string,
): Promise<Array<string> | null>
```
