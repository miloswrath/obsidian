## Deliverables for Tues 02-10
---
- git@github.com:miloswrath/spooftify.git
- Friday 2pm
- LLM Out of Pocket Judgement w/ Music API


## Wireframe Sketch
---
<iframe style="border: 1px solid rgba(0, 0, 0, 0.1);" width="800" height="450" src="https://embed.figma.com/design/TsHjnnrY80mBusFc4X7nY8/spooftify?node-id=5-5&embed-host=share" allowfullscreen></iframe>


## Scope
---
***IN SCOPE***
- AI Communication
- API Needs querying for song, artist, genre, length
- SQL integration - langchain sql agent
- embed with streaming

***OUT OF SCOPE***
- logins 
- reviews
- Persistent // saved data

## Workflow
---
- Initial chat for vibe
- Preview and swipe on 15-20 songs
- AI then makes out of pocket judgement about the person

## Hosting
---
- Vercel


## Example API Call
---

***Spotify***
```Typescript
const SONG_ID = "3gLUZdR5wsY57N8noHQR9E";
const BASE_URL = "https://api.spotify.com/v1/tracks";

async function getTrack(songId: string) {
  const response = await fetch(`${BASE_URL}/${songId}`, {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
      // Authorization not here for now
	  
    },
  });

  if (!response.ok) {
    throw new Error(`Spotify API error: ${response.status} ${response.statusText}`);
  }

  return response.json();
}

// example usage
getTrack(SONG_ID)
  .then(track => console.log(track))
  .catch(err => console.error(err));
```

***Groq***

```Typescript
from openai import OpenAI
import os
client = OpenAI(
    api_key=os.environ.get("GROQ_API_KEY"),
    base_url="https://api.groq.com/openai/v1",
)

response = client.responses.create(
    input="Explain the importance of fast language models",
    model="openai/gpt-oss-20b",
)
print(response.output_text)
```
