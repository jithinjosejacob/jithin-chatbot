---
title: jithin-chatbot-space
app_file: app.py
sdk: gradio
sdk_version: 6.2.0
python_version: "3.11"
---

Deployed to https://huggingface.co/spaces/jithinjacob2011/jithin-chatbot-space

Create at .venv virtual python environment

Create a .env file with below keys
HF_TOKEN
pushover_user
pushover_token

### Local Setup ###

Create pyproject.toml to build uv dependancies - uv init --no-readme --no-workspace

# Install dependencies

uv sync

# Run the app

uv run python app.py

# Remove any binary files from repo


# chroma db documents

View document count

```bash
uv run python -c "from app import me; print(len(me.vectorstore.get()['ids']))"
```

Search for specific content

```uv run python -c "from app import me; docs = me.vectorstore.similarity_search('automation', k=2); print([d.page_content[:100] for d in docs])"```


```bash
# List all collection data with full details
cd /Users/jjj/Desktop/SourceCode/jithin-chatbot && uv run python -c "
from app import me
all_docs = me.vectorstore.get()
print('🎯 Complete ChromaDB Collection Data')
print('=' * 50)
print(f'📊 Total Documents: {len(all_docs[\"ids\"])}')
print(f'📁 Sources: {set(meta.get(\"source\", \"unknown\") for meta in all_docs[\"metadatas\"])}')
print()

for i, (doc_id, content, metadata) in enumerate(zip(all_docs['ids'], all_docs['documents'], all_docs['metadatas']), 1):
    print(f'📄 Document {i}')
    print(f'   ID: {doc_id}')
    print(f'   Source: {metadata.get(\"source\", \"unknown\")}')
    print(f'   Length: {len(content)} characters')
    print(f'   Preview: {content[:200]}...')
    print('-' * 40)
"
```