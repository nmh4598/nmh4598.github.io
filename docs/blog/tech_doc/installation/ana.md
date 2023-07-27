### Installation

To `install` the required packages, follow these steps:

- ``Clone`` :octicons-repo-clone-16: this repository to your local machine

    === "HTTPS"
        ```bash
        git clone https://github.com/nmh4598/ana_soc_net.git
        ```
    === "SSL"
        ```bash
        git clone git@github.com:nmh4598/ana_soc_net.git
        ```

- "Open a `terminal` :octicons-terminal-16: and navigate to the root directory of the repository

- `Create` a virtual environment by running the following command
    ```bash
    python -m venv venv
    ```
- `Activate` the virtual environment:

    === "Windows" :simple-windows:{ .blue }"
        ```bash
        source venv/Scripts/activate
        ```
        
    === "Macbook :simple-apple:{ .gray} or Linux :simple-linux:{ .orange }"
        ```bash
        source venv/bin/activate
        ```

- `Install` the required packages by running:
    ```bash
        pip install -r requirements.txt
        streamlit run src/app.py
    ```
??? " Following this step to install via  ``Docker``:fontawesome-brands-docker:{ .blue } "

    - `Build` the Docker image by running the following command:
        ```bash
        docker build -t my-streamlit-app .
        ```
    - `Run` the Docker container by running the following command:

        ```bash
        docker run -p 8501:8501 my-streamlit-app
        ```
    This will start the Docker container and map port 8501 of the container to port 8501 of your local machine.

-  Finally, `open` a web browser :material-web: and go to [http://localhost:8501](http://localhost:8501/) or you can check my app [Streamlit](https://streamlit.io/) :simple-streamlit:{ .red } here: [Link](https://nmh4598ana.streamlit.app/)

# Class diagrams

``` mermaid
classDiagram
  PyvisGraph <|-- CenCom
  CenCom <|-- Carac
  Carac <|-- Graph
  PyvisGraph: -_add_nodes_and_edges()
  PyvisGraph: +gnet_pyvis()
  class Graph{
        + String edges_path
        + String nodes_path
        + DataFrame edges
        + DataFrame nodes
        + Graph graph 
        + bool rada
        + load_data()
        + create_graph()
        + random_graph()
        + choose_data()
    }
  class Carac{
        + info()
    }
  class CenCom{
        - _create_centrality_df()
        - _create_communities_df()
        + centrality()
        + communities()
    }
```