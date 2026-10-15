# lana

A Claude Code plugin that turns any topic into a 10-question multiple-choice Kahoot quiz.

1. You give Claude a topic (or say "lana").
2. Claude writes the quiz in chat: 10 questions, 4 answers each, one correct.
3. You approve it or ask for changes.
4. Claude saves it as **one private draft** in your Kahoot account and gives you the editor link. It never hosts, shares or publishes the quiz.

## Requirements

- Claude Code
- The **Kahoot connector**, connected to your Kahoot account (Claude uses it to create the draft)

## Install

Add this marketplace, then install the plugin. Run these inside Claude Code.

From GitHub:

```
/plugin marketplace add tanousjoey-del/lana
/plugin install lana@tanousjoey-del-skills
```

Or from a local copy of this folder:

```
/plugin marketplace add ./lana
/plugin install lana@tanousjoey-del-skills
```

## Use

```
/lana the solar system
```

or just ask: "Make me a Kahoot about the solar system."
