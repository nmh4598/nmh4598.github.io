## Terrorist and random network analysis

This project examines terrorist social networks using data available from data information sources in [Valdis Krebs' article](https://firstmonday.org/ojs/index.php/fm/article/view/941/863). Specifically, we examine the network surrounding the tragic events of [September 11, 2001](https://fr.wikipedia.org/wiki/Attentats_du_11_septembre_2001). The September 11, 2001 attacks were four Islamist suicide attacks carried out on the same day in the :flag_us:United States. With the dataset, we are able to map a part of the network centered around the 19 deceased hijackers. This network gives us an insight into the terrorist organization.

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

### Description
The September 11, 2001 attacks were four Islamist suicide attacks carried out on the same day in the :flag_us:United States, causing the deaths of 2,977 people. They took place in Manhattan, New York, Arlington in Virginia, and Shanksville in Pennsylvania. Nineteen terrorists hijacked four commercial airplanes. Two planes, :material-airplane:{ .airplan1 }<span style="color:#ff4d4d">AA 11</span> and :material-airplane:{ .airplan2 } <span style="color:#990000">UA 175</span>, controlled respectively by <span style="color:#ff4d4d">Mohamed Atta</span> and <span style="color:#990000">Marwan al-Shehhi</span>, were flown into the Twin Towers of the World Trade Center (WTC) in Manhattan (New York), while a third plane was flown into the Pentagon, the headquarters of the Department of Defense, in Washington, D.C., killing all the people on board and many others working in these buildings. The third plane, :material-airplane:{ .airplan3 }<span style="color:#33cc33"> AA 77</span>, controlled by <span style="color:#33cc33">Hani Hanjour</span>, was also flown into the Pentagon. The fourth plane, :material-airplane:{ .airplan4 }<span style="color:#0066cc"> UA 93</span>, controlled by <span style="color:#0066cc">Ziad Jarrah</span>, crashed in a field in Shanksville, Pennsylvania.

<div style="text-align: center;">
  <img src="https://raw.githubusercontent.com/nmh4598/ana_soc_net/master/data/img/airplane.jpg" alt="Airplane image">
</div>

We will discover the formation of terrorist social networks. The "Hamburg cell" was a group of radical Islamists based in Hamburg, :flag_de: Germany on November 1, 1998, which included students from different Arab countries who eventually became key agents in the September 11 attacks. They are the important members: <span style="color:#990000">Marwan al-Shehhi </span>, <span style="color:#0066cc">Ziad Jarrah </span > and <span style="color:#ff4d4d">Mohamed Atta</span>, who led the four hijacking teams, . They arrived in the :flag_us:United States in mid-2000 to conduct flight training. Other members included <span style="color:orange">Said Bahaji, Zakariya Essabar, Mounir el-Motassadeq and Abdelghani Mzoudi</span>. And <span style="color:orange">Ramzi bin al-Shibh</span>, who conspired with the other three members but was unable to obtain a :passport_control: visa to enter the :flag_us: United States. It was later replaced with <span style="color:#33cc33">Hani Hanjour</span>. But the first hijackers to arrive in the :flag_us:United States were <span style="color:#33cc33">Khalid al-Mihdhar</span> and <span style="color:#33cc33"> Nawaf al-Hazmi </span> in January 2000.

### Characteristics

With the data from the table below, we can see that our social network has `62 nodes`, including hijackers and co-conspirators. Thus, the `density` is 0.0804, which is quite `low`, indicating that the graph is sparse and there are relatively few links between nodes. The number of connected components in a graph is equal to 1, meaning that all nodes in the graph are connected to each other by a path. There are no subsets of nodes that are disconnected from each other and cannot be reached from one another. In this case, the graph is a `connected graph`. The average number of links that a node has in the graph, or the average degree, is equal to 4.9. The farthest nodes from each other are separated by 5 links. The average distance between all pairs of nodes is 2.94 links. A clustering coefficient of 0.49 would indicate that the nodes in a network are moderately well-clustered.

|   Number of nodes |   Number of edges | Directed graph   |   Number of Components |   Average degre |   Density |   Diameter of Network |   Average Shortest Path |   Clustering |
|------------------:|------------------:|:-----------------|-----------------------:|----------------:|----------:|----------------------:|------------------------:|-------------:|
|                62 |               152 | False            |                      1 |           4.903 |      0.08 |                     5 |                   2.946 |        0.486 |

**Conclusion**: Les 19 pirates de l'air n'ont pas agi seuls. Ils avaient 43 autres complices qui ne sont pas montés à bord de l'avion. These co-conspirators are money generators and also provide the skills and knowledge needed. Networks expose the hijackers and their network neighborhoods - their direct and indirect associates. There are a total of 152 links between 62 members. It is surprising that there are 10 co-conspirators who have less than 20 direct links with the hijackers (excluding the "Hamburg Cell"). The other co-conspirators have direct and indirect links with the "Hamburg Cell". This indicates that my network seems to be divided into two halves separated by the "Hamburg Cell". The distance between hijackers on the same team is also very low. Many pairs of team members were beyond each other's observability horizon - many on the same flight were more than two steps away from each other. This is like a strategy to keep team members apart from each other and other teams, minimizing damage to the network if a cell member is captured or otherwise compromised.

### Centrality 
=== "Degree centrality" 
    [Degree centrality](https://www.geeksforgeeks.org/degree-centrality-centrality-measure/) is the simplest of the four algorithms we will study. It is based on the degree, which we can find in the previous section. In social networks, degree centrality is a measure of popularity and  can be a good way to guess who is in charge. Degree centrality is a fairly rudimentary example, but the following sections present more complex solutions commonly used in network science. The first three <span    style="color:#ff4d4d">Mohamed Atta </span>, <span style="color:#990000">Marwan al-Shehhi </span>, and <span style="color:#33cc33">Hani Hanjour </span> are pilots, while the 4th pilot <span   style="color:#0066cc">Ziad Jarrah </span> is ranked 7th because he has fewer neighbors compared to the other pilots. <span style="color:#ff4d4d">Mohamed Atta </span>'s degree centrality is 0.36, which is much  higher than the individuals below because he has the most links.

    | Index | Degree centrality | Person|
    |-------|-------------------|-----------------------|
    | 11    | 0.360656          | <span style="color:#ff4d4d">Mohamed Atta</span>     |
    | 31    | 0.295082          | <span style="color:#990000">Marwan al-Shehhi </span>|
    | 43    | 0.213115          | <span style="color:#33cc33">Hani Hanjour</span>     |
    | 44    | 0.180328          | <span style="color:#33cc33"> Nawaf al-Hazmi </span> |
    | 1     | 0.180328          | <span style="color:orange">Essid Sami Ben Khemais</span> |
    | 24    | 0.163934          | <span style="color:orange">Ramzi bin al-Shibh</span>|
    | 30    | 0.147541          | <span style="color:#0066cc">Ziad Jarrah</span>      |
    | 40    | 0.147541          | <span style="color:orange">Abdul Aziz Al Omari</span>    |

=== "Closeness centrality"     
    The goal of [closeness centrality](https://www.geeksforgeeks.org/closeness-centrality-centrality-measure/) is to study whether the node is close to other node and can interact with them quickly. The idea is to look at the distance between the nodes. The closeness centrality increases if its distance to other nodes is low. The first three <span style="color:#ff4d4d">Mohamed Atta </span>, <span style="color:#990000">Marwan al-Shehhi </span>, and <span style="color:#33cc33">Hani Hanjour </span> are pilots, while the 4th pilot <span style="color:#0066cc">Ziad Jarrah </span> does not appear because the distance to other nodes is high. <span style="color:#ff4d4d">Mohamed Atta </span>'s distance to other nodes is lower because his closeness centrality is equal to 0.58, which is the highest.

    | Index | Closeness centrality | Person|
    |-------|----------------------|---------------------------|
    | 11    | 0.580952             | <span style="color:#ff4d4d">Mohamed Atta</span>     |
    | 31    | 0.462121             | <span style="color:#990000">Marwan al-Shehhi </span>|
    | 43    | 0.442029             | <span style="color:#33cc33">Hani Hanjour</span>     |
    | 44    | 0.438849             | <span style="color:#33cc33"> Nawaf al-Hazmi </span> |
    | 15    | 0.432624             | <span style="color:#33cc33">Zacarias Moussaoui</span>|
    | 24    | 0.432624             | <span style="color:orange">Ramzi bin al-Shibh</span>|
    | 1     | 0.429577             | <span style="color:orange">Essid Sami Ben Khemais</span> |
    | 40    | 0.420690             | <span style="color:orange">Abdul Aziz Al Omari</span>   |

=== "Betweenness centrality" 
    [Betweenness centrality](https://www.geeksforgeeks.org/betweenness-centrality-centrality-measure/) is based on the assumption that the higher the number of shortest paths passing through a node, the more it acts as a broker (or a bridge). To calculate betweenness centrality, the shortest paths between each pair of nodes are found. The betweenness centrality value for a node or an edge is simply the number of these paths that pass through it. The goal of betweenness centrality is to measure how important a node is in connecting two other nodes in the graph or how a node serves as an intermediary. It also measures the usefulness of the node in communication and information transfer within the graph. The statistics of <span style="color:#ff4d4d">Mohamed Atta </span> are much higher than the others because he plays an important intermediary role in the network. Meanwhile, <span style="color:orange">Essid Sami Ben Khemais </span> and <span style="color:orange">Zacarias Moussaoui</span> are the ones who link <span style="color:#ff4d4d">Mohamed Atta </span> to other co-conspirators. So, they have just a slightly higher measure than the other pilots. Similar to the previous measure, the 4th pilot <span style="color:#0066cc">Ziad Jarrah </span> does not appear on the list.

    | Index | Betweenness centrality| Person                                                   |
    |-------|-----------------------|----------------------------------------------------------|
    | 11    | 1074.215573           | <span style="color:#ff4d4d">Mohamed Atta</span>          |
    | 1     | 459.973443            | <span style="color:orange">Essid Sami Ben Khemais</span> |
    | 15    | 415.416667            | <span style="color:#33cc33">Zacarias Moussaoui</span>    |
    | 44    | 281.939683            | <span style="color:#33cc33"> Nawaf al-Hazmi </span>      |
    | 43    | 230.985462            | <span style="color:#33cc33">Hani Hanjour</span>          |
    | 17    | 221.583333            | <span style="color:orange">Djamal Beghal</span>          |
    | 31    | 162.933836            | <span style="color:#990000">Marwan al-Shehhi </span>     |
    | 39    | 92.178125             | <span style="color:orange">Satam Suqami</span>           |

=== "Eigenvector centrality" 
    [Eigenvector centrality](https://www.geeksforgeeks.org/eigenvector-centrality-centrality-measure/) is based on the analysis of the eigenvectors of the adjacency matrix of a graph. This measure is often used to identify community leaders in social networks. The interesting thing is that the 4th person <span style="color:#0066cc">Ziad Jarrah </span> is also the 4th pilot  because he is connected to the other 3 important pilots. A higher eigenvector score for Mohamed Atta means that he is connected to many nodes that themselves have high scores. We can also see that the other nodes are all very close to each other, they are not separated like in the previous three algorithms.

    | Index | Eigenvector centrality | Person |
    |-------|------------------------|------------------------------------------------------|
    | 11    | 0.412506               | <span style="color:#ff4d4d">Mohamed Atta</span>      |
    | 31    | 0.399862               | <span style="color:#990000">Marwan al-Shehhi </span> |
    | 43    | 0.246944               | <span style="color:#33cc33">Hani Hanjour</span>      |
    | 30    | 0.241743               | <span style="color:#0066cc">Ziad Jarrah</span>       |
    | 40    | 0.238062               | <span style="color:orange">Abdul Aziz Al Omari</span>|
    | 24    | 0.223737               | <span style="color:orange">Ramzi bin al-Shibh</span> |
    | 29    | 0.215109               | <span style="color:orange">Said Bahaji </span>       |
    | 35    | 0.202387               | <span style="color:orange">Fayez Ahmed </span>       |

=== "Comparison"
    | Index| La centralité de degré       | La centralité de proximité   | La centralité intermédiaire | La centralité vecteur propre |
    |----|------------------------------|-------------------------------|------------------------------|------------------------------|
    | 11 | <span style="color:#ff4d4d">Mohamed Atta</span> | <span style="color:#ff4d4d">Mohamed Atta</span> | <span style="color:#ff4d4d">Mohamed Atta</span> | <span style="color:#ff4d4d">Mohamed Atta</span> |
    | 31 | <span style="color:#990000">Marwan al-Shehhi </span>| <span style="color:#990000">Marwan al-Shehhi </span>| <span style="color:#990000">Marwan al-Shehhi </span>| <span style="color:#990000">Marwan al-Shehhi   </span>|
    | 43 | <span style="color:#33cc33">Hani Hanjour</span>  | <span style="color:#33cc33">Hani Hanjour</span>| <span style="color:#33cc33">Hani Hanjour</span>| <span style="color:#33cc33">Han Hanjour</span>|
    | 44 | <span style="color:#33cc33">Nawaf al-Hazmi </span>| <span style="color:#33cc33">Nawaf al-Hazmi </span>| <span style="color:#33cc33">Nawaf al-Hazmi </span> | -1                           |
    | 1  | <span style="color:orange">Essid Sami Ben Khemais </span>       | <span style="color:orange">Essid Sami Ben Khemais  </span>      | <span style="color:orange">Essid Sami Ben Khemais  </span>       | -1                           |
    | 24 | <span style="color:orange">Ramzi bin al-Shibh</span> | <span style="color:orange">Ramzi bin al-Shibh</span> | -1   | <span style="color:orange">Ramzi bin al-Shibh</span>|
    | 30 | -1                           | <span style="color:#0066cc">Ziad Jarrah</span>      | -1                           | <span style="color:#0066cc">Ziad Jarrah</span>      |
    | 40 | <span style="color:orange">Abdul Aziz Al Omari</span>         | <span style="color:orange">Abdul Aziz Al Omari</span>        | -1                           | <span style="color:orange">Abdul Aziz Al Omari</span>          |
    | 15 | -1                           | <span style="color:#33cc33">Zacarias Moussaoui</span>| <span style="color:#33cc33">Zacarias Moussaoui</span>| -1                           |
    | 17 | -1                           | -1                            | <span style="color:orange">Djamal Beghal </span>               | -1                           |
    | 39 | -1                           | -1                            | <span style="color:orange">Satam Suqami </span>                       | -1                           |
    | 29 | -1                           | -1                            | -1                           | <span style="color:orange">Said Bahaji </span>                  |
    | 35 | -1                           | -1                            | -1                           | <span style="color:orange">Fayez Ahmed</span>                   |

**Conclusion**: We see the 3 first pilots appear 4 times in the table above, which confirms that these 3 pilots played an important role. Unlike the other pilots, <span style="color:#33cc33">Nawaf al-Hazmi </span> was considered the second-in-command of the attack. He also initially underwent pilot training but did not complete it. As we know, there were only 19 hijackers. <span style="color:orange">Ramzi bin al-Shibh</span> was selected as the "20th hijacker" to be one of the pilots, but was unable to enter the US. Both of these individuals have links to <span style="color:#ff4d4d">Mohamed Atta </span>, but <span style="color:#33cc33">Nawaf al-Hazmi </span> does not have the same links to other pilots like <span style="color:orange">Ramzi bin al-Shibh</span> who have high eigenvector centrality scores. Therefore, <span style="color:#33cc33">Nawaf al-Hazmi </span> does not appear on the eigenvector centrality list.

### Community

The main goal of community detection is to partition the nodes of a graph into a finite number of groups and to find homogeneous groups of nodes, meaning individuals with similar behavior. By community, we mean a subset of nodes that are strongly connected, i.e., there are a significant number of connections between them, more than what these nodes have with other members of the network. We can quickly find a link between the hijackers and also discover some of the associates of the hijackers. Being associated with a terrorist does not prove guilt, but it can help the investigation process.


The properties of the `Clauset-Newman-Moore` and `Girvan-Newman` algorithms are similar, but the `Girvan-Newman` algorithm focuses more on analyzing links in the network to identify communities, while the `Clauset-Newman-Moore` algorithm focuses on analyzing nodes. The `Louvain` algorithm is generally considered to be faster and more efficient than the `Clauset-Newman-Moore` and `Girvan-Newman` algorithms because it does not require specifying a number of communities in advance and is able to find communities of varying sizes. To construct a clandestine network, one must identify task and trust links between conspirators. These networks often do not behave like normal social networks. Conspirators do not form many links outside of their immediate cluster and often minimize activation of existing links within the network. Tight links between previous contacts, often formed years ago in school and training camps, keep the cells linked. Yet, unlike normal social networks, these strong links largely remain dormant and thus hidden to outsiders.

## References and useful links

Uncloaking Terrorist Networks by Valdis E.Krebs: 
[https://journals.uic.edu/ojs/index.php/fm/article/view/941/863](https://journals.uic.edu/ojs/index.php/fm/article/view/941/863)

"Mapping networks of terrorist cells.\" Connections 24, 43-52 (2002):
[http://insna.org/PDF/Connections/v24/2001_I-3-7.pdf ](http://insna.org/PDF/Connections/v24/2001_I-3-7.pdf )

Network catlogue, repository and centrifuge data Netzschleuder: [https://networks.skewed.de/net/terrorists_911](https://networks.skewed.de/net/terrorists_911)

Network Analysis & Visualisation: Game of Thrones Character Network [Link](https://medium.com/analytics-vidhya/network-analysis-visualization-game-of-thrones-character-network-dc96ea3013e9)