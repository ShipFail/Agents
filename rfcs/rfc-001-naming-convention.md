---
id: RFC-001
slug: naming-convention
title: Consistent Naming Convention for Multi-Tech Stack
author: Huan Li
status: Proposed
created: 2025-09-20
updated: 2025-09-20
tags: ["naming", "style-guide", "shipfail"]
---

## Summary

This RFC defines a **consistent naming convention** for the Ship.Fail umbrella project, which spans across multiple technologies: **Swift (iOS)**, **TypeScript (Firebase)**, **RESTful APIs**, and **Firestore**. The goal is to maintain uniformity and reduce cognitive load by adopting a single naming convention across all layers of the stack.

## Motivation

In a multi-stack environment, inconsistent naming leads to confusion, unnecessary translation between layers, and potential errors. A unified approach:

* Enhances **developer productivity**.
* Improves **maintainability**.
* Supports **AI-assisted coding agents** by reducing ambiguity.

## Specification

### Global Naming Rules

* **camelCase** is the default style across all layers.
* **PascalCase** is used for **classes** and **interfaces**.
* **kebab-case** is used for **file names**, except for class/interface files.

### Component Conventions

| **Component**                    | **Convention**                                             |
| -------------------------------- | ---------------------------------------------------------- |
| **Variables**                    | camelCase (iOS, TypeScript, Firestore)                     |
| **Constants**                    | camelCase (or UPPER\_SNAKE\_CASE for global constants)     |
| **Classes / Interfaces**         | PascalCase (TypeScript and Swift)                          |
| **Files (TypeScript)**           | kebab-case (except files containing classes or interfaces) |
| **Files (Swift)**                | PascalCase (for files containing classes or interfaces)    |
| **REST API Routes**              | camelCase (for route paths and parameters)                 |
| **API Parameters**               | camelCase (query parameters and URL parameters)            |
| **JSON Keys (Req/Resp)**         | camelCase (for consistency across frontend and backend)    |
| **Firestore Collections/Fields** | camelCase (for collections and document fields)            |

### Examples

1. **Swift (iOS)**: The app uses `userProfile` and sends a request with the `userId` parameter.
2. **REST API (TypeScript/Firebase)**: Processes the request and accesses Firestore using `userProfile`.
3. **Firestore**: Stores fields such as `userId`, `userProfile`, and `userStatus`.
4. **Response**: Returns JSON with camelCase keys, e.g. `userProfile`.

## Rationale

* **Consistency**: camelCase across layers reduces the need for translation.
* **Clarity**: PascalCase for classes/interfaces aligns with OOP practices.
* **Readability**: kebab-case file names are standard in TypeScript for non-class files.
* **Platform Alignment**: Swift’s style guide uses PascalCase for class/interface files.

## Benefits

* **Uniformity**: Single convention across variables, files, APIs, and Firestore.
* **Reduced Cognitive Load**: Developers avoid switching contexts between styles.
* **Maintainability**: Consistent patterns improve onboarding and collaboration.
* **Scalability**: AI agents and human developers share a predictable convention.

## Drawbacks

* May require renaming legacy files and variables.
* Enforcing across diverse teams requires linting and CI/CD rules.

## Alternatives Considered

* **snake\_case for Firestore fields** (rejected: inconsistent with app/API).
* **PascalCase for API routes** (rejected: not idiomatic for REST).
* **Mixed conventions per platform** (rejected: increases cognitive load).

## Adoption Plan

1. Apply convention to all new code.
2. Gradually refactor existing code during active development.
3. Add linting/pre-commit checks to enforce consistency.
4. Document in developer onboarding materials.

## Conclusion

By adopting **RFC-001: Consistent Naming Convention**, Ship.Fail ensures a clean, scalable, and developer-friendly codebase across iOS, Firebase, REST APIs, and Firestore. This alignment improves efficiency and reduces ambiguity for both human and AI contributors.
