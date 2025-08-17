# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a documentation hosting repository for Streamlinity LLC, designed to publicly share technical content and retrospectives. The primary content documents AI-assisted software development experiences using Claude Code.

## Architecture Overview

**Static Documentation Site with Automated Index Generation**
- Documents are stored in `docs/` directory
- GitHub Actions automatically generates `index.html` from document files
- Zero-maintenance publishing workflow with auto-commit/push

## Key Commands

### Environment Setup
```bash
poetry install          # Install minimal Python dependencies
poetry shell            # Activate virtual environment
```

### Content Management
```bash
# Add new documents to docs/ directory - automation handles indexing
# Supported formats: .pdf, .html, .md, .txt, .docx

# Manual workflow trigger (if needed)
gh workflow run generate-index.yaml
```

### Git Operations
```bash
git add -A && git commit -m "descriptive message" && git push
# Note: You have full git permissions configured in .claude/settings.local.json
```

## File Organization

- `docs/` - All documentation content (auto-indexed)
- `index.html` - Auto-generated document index (do not edit manually)
- `.github/workflows/generate-index.yaml` - Index generation automation
- `pyproject.toml` - Poetry configuration (minimal Python setup)

## Workflow Automation

The GitHub Actions workflow:
1. Scans `docs/` for document files on every push
2. Generates HTML index with PST timestamps
3. Auto-commits and pushes updates to `index.html`
4. Uses `find ./docs -name "*.pdf" -o -name "*.html" -o -name "*.md" -o -name "*.txt" -o -name "*.docx"`

## Development Notes

- Place all content in `docs/` directory for automatic indexing
- The workflow handles timezone conversion to Pacific Time
- Copyright notices are configured for public sharing compatibility
- HTML documents include responsive CSS and print optimization
- Repository is optimized for AI-assisted content creation workflows

## YAML Linting

Always run `yamllint` on workflow files before committing:
```bash
yamllint .github/workflows/generate-index.yaml
```