# Module Creation Process

The following page guides you through the process of creating an NDP Module. Take into consideration that the creation of publication of NDP Modules is reserved for contributors with Subject Matter Expert (SME) credentials. 

### Setup

Before creating a module, ensure you have completed the following steps:

1. **Register your dataset:** Identify or [register](../catalog/register-data.md) the dataset for your module in the [NDP catalog](https://nationaldataplatform.org/ckandata).  
2. **Prepare your code repository**: Set up a GitHub repository containing all the necessary notebooks, helper scripts, and `requirements.txt` files for the correct execution of your module in JupyterLab. The following [repository]() provides an example. 
3. **Prepare your model repository**: If your module uses a model available through HuggingFace or GitHub, prepare the `.git` link for its inclusion into your module.

### Module creation

1. Go to the *Educator's Portal* within the NDP Education Hub. 
2. Click on *Add New Module*. 
3. Fill in main module information:
    - **Title:** The title of your module. 
    - **Institution:** The name of your institution.
    - **Description:** This section must introduce the module in 2-3 paragraphs, covering the topics, data, and model(s) used, while capturing the learner's interest.
    - **Instructions:** This section must provide clear, step-by-step guidance for learners on how to navigate and complete the module. They outline the flow of activities to support successful completion.
    - **Learning Objectives:** This section must summarize the key skills, knowledge, and tasks learners will acquire or accomplish by the end of the module. Use 3-5 bullet points to clearly state the expected learning outcomes.
4. Add the following supporting information:
    - **Tags:** Add tags the support the search of your module.
    - **Skills:** List the skills that learners will acquire through your module. 
    - **Prerequisites:** Outline the prerequisites for learners to properly interact with your module. 
    - **Additional Resources:** Provide URLs that link to supportive information and resources for your module.
    For the addition of each of the supporting information labels, write the label 
5. Click the **Datasets** section and search for your dataset in the NDP catalog. Add it to your module by clicking the Add button. Note that this window only supports *Substring Search*.
6. In the **Models section**, attach the `.git` link of the model used in your module, if applicable.
7. In the **Scripts section**, attach the `.git`link to your GitHub repository. 
8. Save your module. 

### Module Publication

When you are finished creating your module, you can publish it to make it available for inclusion in a classroom or data challenge. Once you publish your module, **you will not be able to make any further changes**. 