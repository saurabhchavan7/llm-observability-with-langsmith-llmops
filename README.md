# LangSmith Observability and LLMOps

This repository contains hands-on LangSmith examples and documentation for tracing, debugging, monitoring, and evaluating LLM-based applications.

The goal of this repository is to explain how LangSmith helps understand what happens inside complex LLM systems such as simple chains, RAG applications, agents, and LangGraph workflows.

## What This Repository Covers

This repository focuses on the role of LangSmith in production-style LLM applications, especially where debugging and monitoring become difficult due to multiple components, non-deterministic outputs, latency issues, token usage, cost spikes, and hallucinations.

The main topics covered include:

- Why observability is needed in LLM applications
- Common production issues in LLM systems
- LangSmith projects, traces, and runs
- Tracing simple LangChain applications
- Tracing sequential LLM chains
- Adding custom tags, metadata, and run names
- Debugging RAG applications using LangSmith
- Understanding retriever and generator failures
- Tracing custom Python functions using `@traceable`
- Improving RAG latency using reusable vector indexes
- Tracing agentic workflows and tool calls
- Understanding ReAct-style agent execution
- LangSmith integration with LangGraph
- Tracking graph execution, nodes, and intermediate states
- Monitoring and alerting across multiple traces
- Evaluation of LLM outputs
- Prompt experimentation and comparison
- Dataset creation and annotation
- User feedback collection
- Collaboration features for teams
- Introduction to LLMOps concepts

## Why LangSmith Matters

LLM applications are often difficult to debug because they are not simple one-step systems. A single user request may go through multiple stages such as prompt creation, retrieval, LLM calls, output parsing, tool usage, or graph-based execution.

When something goes wrong, such as high latency, increased cost, hallucination, or poor answer quality, it is not always clear which component caused the issue.

LangSmith helps solve this problem by making the internal execution of an LLM application visible. It records the input, output, latency, token usage, cost, errors, metadata, and intermediate steps of each component.

This makes it easier to debug, monitor, evaluate, and improve LLM applications.

## Core Concepts

### Project

A project represents an LLM application or workflow being tracked in LangSmith.

For example, a simple chatbot, a RAG chatbot, an agent, or a LangGraph workflow can each be treated as a separate project.

### Trace

A trace represents one complete execution of an application.

For example, when a user asks a question and the full application runs from input to final output, that complete execution is stored as one trace.

### Run

A run represents the execution of one component inside a trace.

For example, a prompt template, LLM call, retriever, output parser, tool call, or LangGraph node can each appear as a run inside a trace.

## Example Use Cases

### 1. Debugging Latency Issues

In a complex LLM workflow, latency may suddenly increase from a few seconds to several minutes. Without observability, it is difficult to know whether the delay came from document loading, retrieval, prompt generation, LLM response time, or output parsing.

LangSmith helps identify which component is taking extra time.

### 2. Tracking Cost and Token Usage

Agentic systems may repeat steps multiple times depending on their reasoning process. This can increase token usage and cost.

LangSmith helps track token consumption, cost, and repeated execution patterns.

### 3. Debugging RAG Hallucinations

A RAG system may produce incorrect answers because:

- The retriever fetched irrelevant documents
- The generator ignored the context
- The prompt did not strongly enforce context-based answering

LangSmith helps inspect the retrieved documents, final prompt, and LLM response to identify the root cause.

### 4. Understanding Agent Behavior

Agents can call tools, observe results, update their scratchpad, and continue reasoning.

LangSmith helps visualize each step of the agent loop, including tool selection, tool input, tool output, and final answer.

### 5. Tracing LangGraph Workflows

In LangGraph, an LLM workflow is represented as a graph with nodes and edges.

LangSmith helps trace the full graph execution. Each graph execution becomes a trace, and each node execution becomes a run.
