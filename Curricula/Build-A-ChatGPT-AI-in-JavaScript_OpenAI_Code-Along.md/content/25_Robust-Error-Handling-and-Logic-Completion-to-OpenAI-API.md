# 25. [Robust Error Handling and Logic Completion to OpenAI API

-   empty input error
```
if (!animal.trim().length) {
    res.status(400).json({
        error:{
            message:"Please enter a valid animal"
        }
    });
    return;
}
```

- try catch wrap the response
```
  try {
    const response = await openai.createCompletion({
      model: "text-davinci-003",
      prompt: `suggest three pet names for the follow ${animal}`,
      temperature: 0.8,
      max_tokens: 100,    
    });
    res.status(200).json({result: response.data.choices[0].text});
  } catch (error){
    if(error.response){
      console.log(error(error.response.status, error.response.data));
      res.status(error.response.status).json(error.response.data);
    } else {
      console.error(`Error with OpenAI API request: ${error.message}`);
      res.status(500).json({
        error: {
          message: 'An error occured during your request'
        },
      });
    };
  };  
```