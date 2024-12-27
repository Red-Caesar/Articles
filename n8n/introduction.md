# Exploring Workflow Automation with n8n: A Deep Dive into Sensitive Data Removal and AI Integration

Hello! Today, we’re diving into the world of workflow automation with [n8n](https://n8n.io/), a powerful and flexible tool that’s gaining traction among teams and organizations looking to streamline their processes. Whether you’re automating complex business workflows or simplifying personal tasks, n8n offers a robust platform to get the job done efficiently.

## What is n8n?

At its core, n8n is an open-source workflow automation tool that provides a web-based interface for creating and managing automated workflows. Its strength lies in its extensive library of pre-built nodes, which allow users to connect various apps, services, and APIs without writing a single line of code. This makes it an ideal choice for teams looking to automate repetitive tasks, integrate disparate systems, or even incorporate AI into their workflows.

While n8n is still a developing project, its current capabilities are already impressive. With over 1,000 pre-existing [workflows](https://n8n.io/workflows/) created by the community, users have a wealth of templates to draw inspiration from. Although the platform may not yet cover every possible scenario for data manipulation, its active development ensures that new features and nodes are continually being added.

## Our Project: Sensitive Data Removal with AI

At our company, we’ve been working on an exciting project that involves the removal of sensitive data from documents. The cornerstone of this project is **llama-3.2**, a fine-tuned AI model capable of identifying and removing 20 different types of sensitive information through functional calls. To enhance this project, we’ve explored two potential use cases for n8n, which we’ll walk you through below.

---

### Case #1: Cleaned Database and Vector Search

One of our clients approached us with a specific need: they wanted to remove sensitive data from their documents and store the cleaned versions in a database. Beyond that, they had several use cases in mind for the database, such as improving their customer support service. For example, when a service provider assists a client, they could consult the database for previous similar cases and develop a strategy to resolve the issue more effectively.

To achieve this, we divided the system into two main parts:

1. **Creating a Database and Building a Vector Store**  
   Our tool, running locally on port 9090, processes the documents and replaces sensitive data with `****`. The cleaned documents are then saved in both a database and a vector store. Here’s a glimpse of the process:

   ![alt text](images/create_vector_store.png)  
   *Sensitive data is replaced with `****`.*  
   ![alt text](images/cleaned_messages.png)  
   *The cleaned documents are saved in the database.*  
   ![alt text](gifs/create_db.gif)  
   *The complete process of creating the database and vector store.*

2. **Extracting Necessary Documents**  
   Using n8n’s chat node, we can submit a request to the vector database and retrieve the relevant documents. Here’s how it works:

   ![alt text](images/search.png)  
   *Submitting a request to the vector database.*  
   ![alt text](images/health_report.png)  
   *Receiving the search results.*  
   ![alt text](gifs/vector_search.gif)  
   *The full process of document extraction.*

---

### Case #2: Continuous Testing and Evaluation

Our project is still in development, and we’re constantly adding new heuristics to improve the detection of sensitive data. To ensure the system’s accuracy, we need to conduct continuous testing. n8n provides a good opportunity for this with its time-based and other types of triggers.

For instance, we’ve set up a trigger that activates whenever a test file is added to a specific folder. Our project already includes a basic command-line interface for running tests, which reads data from a user-specified file and outputs the results to the console. We’ve integrated this interface into n8n to streamline the testing process.

Here’s how it works:

1. **Preparing Parameters for Evaluation**  
   We specify the initial settings for the service in the `prepare parameters for evaluation` node and save them in the `auto_config.json` file.  
   ![alt text](images/test_pipeline.png)  
   *Setting up the evaluation parameters.*

2. **Running the Evaluation**  
   The path to the `auto_config.json` file is submitted to the testing interface through the n8n `run evaluation` node.  
   ![alt text](images/test_execute.png)  
   *Executing the evaluation process.*

3. **Analyzing the Results**  
   n8n offers several options for storing test results, including APIs, Google Sheets, and local storage. For better visualization, we chose to plot a graph. Here’s what the results look like:  
   ![alt text](images/chart.png)  
   *Visualizing the test results.*  
   ![alt text](gifs/test_pipeline.gif)  
   *The complete testing process.*

---

## Conclusion

n8n has proven to be an invaluable tool for automating workflows, especially when combined with AI technologies.

If you're interested in our sensitive-data-removal app, you can give it a try by using the following command:

```bash
curl -X POST http://www.aibench.xyz/clean/ -H "Content-Type: application/json" -d '{"prompt": "My card id 1235134"}' -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoidGVzdCIsImxpbWl0Ijo1MDAwfQ.KArlxrfixVv7Zono7u8r2l2DJT06MiaZSOtIm-I_yTQ" 
```

If you’re working on similar projects or have other AI-related initiatives, we’d love to hear from you! Feel free to reach out to us—we’re always excited to collaborate on innovative solutions and explore new possibilities in the world of automation and AI.