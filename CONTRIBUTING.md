# Contributing to ChromaFlow

Thank you for your interest in contributing to ChromaFlow! 🎉

We welcome contributions from everyone. This document provides guidelines for contributing to the project.

## 📖 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [How to Contribute](#how-to-contribute)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Commit Messages](#commit-messages)
- [Pull Request Process](#pull-request-process)

## 🤝 Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct:

- Be respectful and inclusive
- Welcome newcomers and help them learn
- Focus on what is best for the community
- Show empathy towards other community members

## 🚀 Getting Started

### Prerequisites

- Node.js 20+ and npm/yarn
- Python 3.11+
- Docker & Docker Compose
- Git
- PostgreSQL 15+
- Redis 7+

### Fork and Clone

1. Fork the repository on GitHub
2. Clone your fork locally:
```bash
git clone https://github.com/YOUR-USERNAME/ChromaFlow.git
cd ChromaFlow
```

3. Add the upstream repository:
```bash
git remote add upstream https://github.com/KaizerAE/ChromaFlow.git
```

4. Install dependencies:
```bash
# Frontend
cd frontend && npm install

# Backend
cd ../backend && npm install

# AI Engine
cd ../ai-engine && pip install -r requirements.txt
```

## 📝 How to Contribute

### Reporting Bugs

Before creating a bug report:
- Check if the issue already exists
- Collect relevant information (OS, versions, error messages)

Include in your bug report:
- Clear title and description
- Steps to reproduce
- Expected vs actual behavior
- Screenshots if applicable
- Environment details

### Suggesting Features

We love new ideas! When suggesting features:
- Check if it's already been suggested
- Explain the problem you're trying to solve
- Describe your proposed solution
- Consider alternative solutions

### Contributing Code

1. Check the [issue tracker](https://github.com/KaizerAE/ChromaFlow/issues) for open issues
2. Comment on an issue to claim it
3. Wait for approval before starting work
4. Follow the development workflow below

## 🛠️ Development Workflow

### 1. Create a Branch

```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/your-bug-fix
```

Branch naming conventions:
- `feature/` - New features
- `fix/` - Bug fixes
- `docs/` - Documentation changes
- `refactor/` - Code refactoring
- `test/` - Adding tests

### 2. Make Your Changes

- Write clean, readable code
- Follow coding standards (see below)
- Add tests for new features
- Update documentation as needed

### 3. Test Your Changes

```bash
# Frontend
cd frontend
npm run test
npm run test:e2e
npm run lint

# Backend
cd backend
npm run test
npm run lint

# AI Engine
cd ai-engine
pytest
black .
flake8
```

### 4. Commit Your Changes

Follow our [commit message guidelines](#commit-messages).

### 5. Push and Create PR

```bash
git push origin feature/your-feature-name
```

Then create a Pull Request on GitHub.

## 💯 Coding Standards

### Frontend (TypeScript/React)

- Follow [Airbnb React Style Guide](https://airbnb.io/javascript/react/)
- Use TypeScript for type safety
- Use functional components with hooks
- Keep components small and focused
- Use meaningful variable names
- Write JSDoc comments for complex functions

```typescript
// Good
const calculateTaskPriority = (task: Task): number => {
  return task.urgency * task.importance;
};

// Bad
const calc = (t: any) => t.u * t.i;
```

### Backend (Node.js)

- Use ESLint with provided configuration
- Follow async/await patterns
- Handle errors properly
- Validate inputs
- Write unit tests for services

```typescript
// Good
async function getUserById(id: string): Promise<User> {
  try {
    const user = await User.findById(id);
    if (!user) throw new NotFoundError('User not found');
    return user;
  } catch (error) {
    logger.error(`Error fetching user: ${error}`);
    throw error;
  }
}
```

### AI Engine (Python)

- Follow PEP 8 style guide
- Use Black formatter
- Use type hints
- Write docstrings
- Keep functions focused

```python
# Good
def analyze_code_quality(code: str, language: str) -> Dict[str, Any]:
    """
    Analyze code quality and return metrics.
    
    Args:
        code: Source code to analyze
        language: Programming language
        
    Returns:
        Dictionary containing quality metrics
    """
    # Implementation
    pass
```

## ✉️ Commit Messages

We follow [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
type(scope): subject

body (optional)

footer (optional)
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding tests
- `chore`: Maintenance tasks

### Examples

```
feat(frontend): add voice command feature

fix(backend): resolve JWT token expiration issue

docs(readme): update installation instructions

refactor(ai): optimize code analysis algorithm
```

## 📤 Pull Request Process

### Before Submitting

- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] Tests added/updated
- [ ] All tests pass
- [ ] No merge conflicts

### PR Title

Follow commit message format:
```
feat(scope): add new feature
```

### PR Description Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
Describe tests performed

## Screenshots (if applicable)
Add screenshots

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-reviewed
- [ ] Comments added
- [ ] Documentation updated
- [ ] Tests added
- [ ] All tests pass
```

### Review Process

1. At least one maintainer review required
2. All comments must be resolved
3. All checks must pass
4. Squash and merge when approved

## ❓ Questions?

Feel free to:
- Open an issue for questions
- Join our community discussions
- Reach out to maintainers

## 🙏 Thank You!

Your contributions make ChromaFlow better for everyone. We appreciate your time and effort!

---

Happy Coding! 🚀
