## Phase 1: Integration of Open-Source LLMs in Synapse Copilot

### HuggingFace Inference API for Free Access to Open Source Models by API
We replaced the default OpenAI llm with Huggingface Inference API endpoints. 
Which allows to make api calls to some open source models hosted by huggingface. 
You can replace the repo_id with another model's name available on huggingface through inference api.
``` python
os.environ["HUGGINGFACEHUB_API_TOKEN"] = 'your hugging face token'
from langchain_community.llms import HuggingFaceEndpoint
repo_id = "mistralai/Mistral-7B-Instruct-v0.3"
llm = HuggingFaceEndpoint(
    repo_id=repo_id,
    max_length=128,
    temperature=0.5,
    token=os.environ["HUGGINGFACEHUB_API_TOKEN"],
)
```

One can then pass this llm to api_llm

``` python
api_llm = ApiLLM(
        llm,
        api_spec=api_spec,
        scenario=scenario,
        requests_wrapper=requests_wrapper,
        simple_parser=False,
    )
```

## Using Prompt Engineering to get high performance out of Small Models: Mixtral 7b mistralai/Mistral-7B-Instruct-v0.3
### Multiple examples to get higher accuracy with small model
We learned that using multiple examples for an endpoint can greatly improve the accuracy of synapse-copilot. @Homan used multiple examples for Github creation
and that results in this query now working accurately > 80% of the time (we ran this more than 50 times during development and can use it smoothly). 

```
Example 1:
Background: User wants to create a simple public repository.
User query: Create a new repository named 'hello-world'.
API calling 1: POST /user/repos with {"name": "hello-world", "private": false}
API response: {"id": 123, "name": "hello-world", "full_name": "username/hello-world", "private": false}
Final Answer: Repository 'hello-world' created successfully.

Example 2:
Background: User wants to create a private repository with a description.
User query: Create a private repository named 'secret-project' with a description 'Confidential project repository'.
API calling 1: POST /user/repos with {"name": "secret-project", "private": true, "description": "Confidential project repository"}
API response: {"id": 124, "name": "secret-project", "full_name": "username/secret-project", "private": true}
Final Answer: Private repository 'secret-project' created successfully with description 'Confidential project repository'.

Example 3:
Background: Handling creation failure due to missing repository name.
User query: Create a repository without specifying a name.
API calling 1: POST /user/repos with {"name": ""}
API response: {"message": "Validation Failed", "errors": [{"resource": "Repository", "field": "name", "code": "missing_field"}]}
Final Answer: Failed to create repository. Error: Name is required.

Example 4:
Background: No background
User query: Create a new public repository named "test-repo"
API calling 1: POST /user/repos to create a repository named "test-repo"
API response: Repository "test-repo" created successfully
``` 

### Bigger model for Precision Tasks: Mixtral 8x7b (mistralai/Mixtral-8x7B-Instruct-v0.1)
For our bigger model we chose Mixtral 8x7B. 

* Free Hugging Face Inference Endpoints have limitations Other large models require Pro subscription. 
* Mixtral 8x7b has higher performance because of 8x7b algorythm splitting feedforward in 8 layers

![Pro subscription](https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/ce75cff4-e236-4420-b227-eff05bb42a3c)
https://arxiv.org/abs/2401.04088

For trello board creation and collaboration adding the 
**Small model chose wrong endpoint at api-selector part**
![Mistral 7B wrong endpoint selected](https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/21af8538-05f4-4ce8-b93f-68f318f44d1b)

**Big Model chooses the right one **
![Mistral 8x7b trello board](https://github.com/Jaswir/Hackathon-Kickstarter-Kit/assets/15957528/b1440bed-1a7a-42dd-b399-443183fbe910)