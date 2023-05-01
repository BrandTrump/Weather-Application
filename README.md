## Credit
Tutorial by [Sonny Sangha](https://www.youtube.com/@SonnySangha) - https://www.youtube.com/watch?v=DS5TZCn-pk8&t=9058s

### Created With
- Next.js 13.3
- [Tremor 2.0](https://www.tremor.so/)
- Tailwind CSS
- TypeScript
- Stepzen
- GraphQL

### Learnings
- How to use StepZen to easily create a GraphQL interface with the [weather API](https://open-meteo.com/)
- How to utilise Apollo to connect with GraphQL backend
- How to use the Tremor React libray 
- How to setup a role for the Openai's model response: 
```js
export async function POST(request: Request) {
  const { weatherData } = await request.json();

  const response = await openai.createChatCompletion({
    model: "gpt-3.5-turbo",
    temperature: 0.8,
    n: 1,
    stream: false,
    messages: [
      {
        role: "system",
        content:
          "Pretend you're a Meteorologists who is reporting on the weather. Introduce yourself as a 
          weather reporter. Then give a very short summary of todays weather only. Make the summary
          easy to understand. Assume the data came from your own research team. End the summary of 
          todays weather with a short joke about the weather.",
      },
      {
        role: "user",
        content: `Hi there, can I get a summary of todays weather, use the following information to 
        get the weather data: ${JSON.stringify(
          weatherData
        )}`,
      },
    ],
  });
  ```
