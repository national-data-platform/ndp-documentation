# Participating in a NDP Data Challenge

Participating in NDP Data Challenges is an excellent opportunity to collaborate on the development of scientific workflows and explore innovative solutions to complex problems.

## Joining a Data Challenge

1. **Log in to NDP**
    - Ensure you have an active account and credentials to access the platform.
2. **Explore Challenges**
    - Navigate to the *Education Hub* and select [Explore](https://nationaldataplatform.org/educationhub/explore). Challenges are listed according to their publication dates.
3. **Select a Challenge**
    - Once you find a challenge that interests you, click *Open* to view its details.

4. **Review Information**
    - Carefully read all the details and instructions before joining a challenge. Joining a challenge involves the allocation of resources, so ensure it aligns with your availability and goals.

5. **Join the Challenge**
    - Click *Join Data Challenge* to initiate team creation.
    - By default, you will be added to your team as the first member.
    - If the challenge permits individual participation, you can name your team and proceed.

6. **Add Team Members**
    - Enter the emails of your team members, preferably academic accounts.
    - Ensure that none of the emails are associated with another active team in the same challenge, as this will prevent team creation.

7. **Confirm Participation**
    - Upon successful team creation, you and your team members will become active participants in the challenge.

## Participating in a Data Challenge

Once you join a challenge, follow these steps to maximize your participation:

### Working with Modules

- Each team is assigned the challenge's [modules](../ndp-modules/index.md) as new [workspaces](../workspace/index.md).
- These modules will appear as workspaces in the [Jupyter widget](../jupyter/widget.md) on JupyterHub.
- Teams can enhance their workflows by adding additional data from the catalog and integrating custom code.

### Working on JupyterHub

- Before starting, thoroughly review the instructions for the data challenge and each module, especially those related to resource reservations.
- Follow the guidelines to optimize resource usage and align with the challenge's objectives.

**NOTE**: If you’re unfamiliar with NDP workspaces, we highly recommend reviewing this brief [tutorial](../workspace/set-up.md) to get started.

### Storage

- Each NDP user is allocated **10GB of persistent storage** on JupyterHub labeled as `_User-Persistent-Storage_`. This storage is private and remains available across sessions. 
- When you join a challenge, your team will receive shared storage labeled as `shared-storage-your-team-name`, also with a **10GB capacity**. Any changes made in this folder are visible to all team members and persist across sessions.

#### Best Practices for Shared Storage

1. **Coordinate File Modifications**
    - Shared storage does not support version control, so avoid simultaneous file edits to prevent conflicts.

2. **Optimize Storage Usage**
    - Use shared storage for frequently accessed code or partial data products essential to your workflow.
   
3. **Avoid File Overwrites**
    - Establish clear team protocols for modifying files to minimize risks of accidental data loss.

!!! note "PVC Policy"
    [Review PVC Policy](../policies/pvc-policy.md)