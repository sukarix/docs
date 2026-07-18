# Release Notes

## Support Policy

Sukarix is currently supported for PHP 8.4+.

## Released versions

- [v0.3.1 - 2026-07-18](#v031)
- [v0.3.0 - 2026-07-17](#v030)
- [v0.2.0 - 2025-01-20](#v020)
- [v0.1.0 - 2024-06-14](#v010)

## v0.3.1

### 🚀 Features

- **Version Number**: 0.3.1
- **Release Date**: 2026-07-18
- **General Overview**: Cursor-based pagination for APIs and cache remember() helper.

### Changes

- **Cursor Pagination**: Added `Response::cursor()` for cursor-based API pagination — stable under concurrent inserts, efficient on large datasets. Returns `{ field, limit, has_more, next }` structure.
- **Cache Remember**: Added `HasCache::remember()` for get-or-set cache pattern and `HasCache::forget()` for invalidation.
- **Paginate Fix**: `Response::paginate()` now casts `pages` to `int` (was `float` from `ceil()`).

## v0.3.0

### 🚀 Improvements & Fixes

- **Version Number**: 0.3.0
- **Release Date**: 2026-07-17
- **General Overview**: Trait initialization refactored, backward compatibility improvements, and test infrastructure.

## v0.3.0

### 🚀 Improvements & Fixes

- **Version Number**: 0.3.0
- **Release Date**: 2026-07-17
- **General Overview**: Trait initialization refactored, backward compatibility improvements, and test infrastructure.

### Changes

- **Trait Initialization**: Moved `Processor::initialize()` from `Tailored::instance()` to class constructors. Each `Tailored` subclass must now call `Processor::instance()->initialize($this)` in its constructor. The `Helper` base class does this automatically.
- **LogWriter**: Added `initLogger()` backward-compatible alias for `initLogWriter()`.
- **TestCase**: Removed `final` keyword to allow subclassing in application test suites.
- **Action**: Added `Processor` import. Made `$view`, `$argv`, `$headerAuthorization`, and `$templatesDir` nullable to prevent uninitialized typed property errors.
- **MailSender**: `smtpSend()` and `generateId()` changed from `private` to `protected` for extensibility.
- **Assets**: Constructor now calls `parent::__construct()` for proper trait initialization.
- **TestScenario**: `loadResult()` handles missing template files gracefully.

## v0.2.0

### 🚀 Features

- **Version Number**: 0.2.0
- **Release Date**: 2025-01-20
- **General Overview**: Added CSRF protection, enhanced session management, and improved validation.

## v0.1.0

### 🚀 Introduction

- **Version Number**: 0.1.0
- **Release Date**: 2024-06-14
- **General Overview**: First version of the Sukarix Framework.
