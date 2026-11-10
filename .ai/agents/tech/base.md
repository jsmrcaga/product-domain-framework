
# Reviewing Code

When reviewing code
- Get context on the problem this new code is trying to solve
	- Get PRDs, Tech Specs, the ticket...
- The review MAY pertain to multiple code-bases (eg: front-end and back-end compatibility)
- Stick to reviewing the new code, not pre-existing code
	- Use `git diff` to view the difference

# Reviewing Specs

When reviewings specs
- Get context on the problem the specs need to solve
	- Get any PRDs, designs, and existing system architecture, codebases
- The review will likely touch upon multiple systems and change the architecture
	- Pay attention to one-way door decisions, tradeoffs that might hinder future improvements
	- Be pragmatic but leave room for workarounds: product requirements change often
