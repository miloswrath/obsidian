#iproj #spoof 


## Constitution md planning
---

***Non-Negotiables***
- Testing suite must cover all primary functions of the application
	- This must be ran each time there is a PR (use github actions)
- Security of private keys must never be leaked, keep in mind the dual usage of `./.envrc` and `./.envrc.local`
- MVP only -> no large production plans -> simplicity is key


## Specify md planning
---

***Goal of the Project***
>Lightweight MVP of a small web-app that takes in user input from a chatbot regarding their "vibe" or what potential music they might like. Then they have a comparison screen where they are to choose between two songs (spotify embeds) which are fetched using the spotify API -> this request's parameters will be determined by the LLM after conversing with the user to determine their vibe - full spec of the API is required knowledge for the AI. Afterwards, the LLM takes in all of the information from the individual and makes an out-of-pocket judgement about the individual.

***What This Requires***
- Groq // open-source LLM integration
- Spotify API integration
- Planned specifications of the API somehow injected into model

***Things to Keep in Mind***
- while this project is an mvp and thus shouldn't focus on optimization, this project should optimize the usage of AI both in its initial user querying stage and its injection of API knowledge extensively using state-of-the-art techniques to lower API // compute costs.
- 







