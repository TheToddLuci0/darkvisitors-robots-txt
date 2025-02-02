# Darkvisitors Robots.txt Action

Automatically add darkvisitors.com's anti-bot things to your robots.txt. 
Caches the results to ensure you don't get your API key bonked.

> Note: This is just a robots.txt file. There's nothing preventing the bots from ignoring it, but the more well behaved ones should follow it.


# Useage


- Create a project at darkvisitors.com and get an access token: https://darkvisitors.com/docs/robots-txt
- Add a secret named DARKVISITORS_API_KEY to your repository with the API key for your project
- Add this repo to your workflow.yml, ideally before any other things that modify robots.txt (to ensure cacheing works cleanly).

```yaml

jobs:
    my-job:
        steps:
            - name: Update robots.txt
              uses: thetoddluci0/darkvisitors-robots-txt@latest
```

## Config

This action supports configring a base file with your existing robots.txt, where to save the file, what to block, and who to block.

A full example:

```yaml
jobs:
    my-job:
        steps:
            - name: Update robots.txt
              uses: thetoddluci0/darkvisitors-robots-txt@latest
              with:
                  # Final save path
                - outfile: static/robots.txt
                  # Base file to append to
                - infile: src/robots_base.txt
                  # What types of agents to deny
                - deny_types: '["Undocumented AI Agent", "AI Assistant"]'
                  # What path to start blocking at
                - disallow: "/super-secret"
```
