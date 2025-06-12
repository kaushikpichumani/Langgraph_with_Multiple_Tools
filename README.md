<h1>LangGraph RAG Selector</h1>

<p>
  This project demonstrates how to use <strong>LangGraph's conditional edge functions</strong> to intelligently decide between using Retrieval-Augmented Generation (RAG) or a base Large Language Model (LLM) to respond to user queries.
</p>

<h2>🧠 Project Overview</h2>
<p>
  The flow works as follows:
</p>
<ol>
  <li>A user submits a query.</li>
  <li>A conditional function determines whether the query falls within the RAG context.</li>
  <li>
    If <code>true</code>, the flow invokes the <strong>RAG module</strong> (vector store + retriever + LLM).
  </li>
  <li>
    If <code>false</code>, the flow routes the request directly to the <strong>LLM</strong>.
  </li>
</ol>

<h2>📦 Components</h2>
<ul>
  <li><strong>LangGraph</strong> – For building the conditional logic graph</li>
  <li><strong>LLM</strong> – Any OpenAI, Anthropic, or HuggingFace model</li>
  <li><strong>RAG</strong> – Retriever + vector store setup for domain-specific content</li>
</ul>

<h2>🔁 Flow Logic</h2>=
<img width="210" alt="image" src="https://github.com/user-attachments/assets/2d12450e-f4f7-4343-b7fe-0e0504fca1d4" />
<h2>🛠️ Setup Instructions</h2>
<ol>
  <li>Clone the repository</li>
  <li>Install dependencies: <code>pip install -r requirements.txt</code></li>
  <li>Configure your API keys and vector store</li>
  <li>Run the LangGraph app: <code>python app.py</code></li>
</ol>

<h2>⚙️ Example Conditional Function</h2>
<pre><code>def is_rag_query(input: dict) -&gt; str:
    question = input["question"]
    if "RAG" in question.lower() or "retrieval" in question.lower():
        return "use_rag"
    return "use_llm"
</code></pre>

<h2>✅ Example Output</h2>
<pre><code>
Input: "How does RAG help in domain-specific search?"
→ Routed to: RAG Chain
→ Answer: "RAG combines external knowledge sources with LLMs..."

Input: "What is the capital of France?"
→ Routed to: LLM Chain
→ Answer: "Paris"
</code></pre>

<h2>📄 License</h2>
<p>This project is licensed under the MIT License.</p>


