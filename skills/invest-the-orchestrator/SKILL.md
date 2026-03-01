# The Orchestrator Skill

## Philosophy
Structured multi-agent coordination using LangGraph to ensure analysis precedes execution.

## Core Principles
- **Parallel Analysis:** Expert analysts run simultaneously.
- **Separation of Concerns:** Data -> Analysts -> Risk -> Portfolio.
- **State Management:** Using `AgentState` to pass signals and metadata.

## Workflow Logic (LangGraph)

```python
def create_workflow(selected_analysts=None):
    """Create the workflow with selected analysts."""
    workflow = StateGraph(AgentState)
    workflow.add_node("start_node", start)
    
    # Add Analyst Nodes
    for analyst_key in selected_analysts:
        workflow.add_node(node_name, node_func)
        workflow.add_edge("start_node", node_name)
        workflow.add_edge(node_name, "risk_management_agent")

    workflow.add_node("risk_management_agent", risk_management_agent)
    workflow.add_node("portfolio_manager", portfolio_management_agent)
    workflow.add_edge("risk_management_agent", "portfolio_manager")
    workflow.add_edge("portfolio_manager", END)
```

## Global Instruction
The entire graph is kicked off with the following directive:
> "Make trading decisions based on the provided data."
