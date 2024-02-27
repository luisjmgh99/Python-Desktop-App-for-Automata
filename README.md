Pythomata
     codecov   

Python implementation of automata theory.

Links
GitHub: https://github.com/whitemech/pythomata
PyPI: https://pypi.org/project/pythomata/
Documentation: https://whitemech.github.io/pythomata
Changelog: https://whitemech.github.io/pythomata/release-history/
Issue Tracker:https://github.com/whitemech/pythomata/issues
Download: https://pypi.org/project/pythomata/#files
Install
from PyPI:
pip install pythomata
or, from source (e.g. develop branch):
pip install git+https://github.com/whitemech/pythomata.git@develop
or, clone the repository and install:
git clone https://github.com/whitemech/pythomata.git
cd pythomata
pip install .
How to use
Define an automaton:
from pythomata import SimpleDFA
alphabet = {"a", "b", "c"}
states = {"s1", "s2", "s3"}
initial_state = "s1"
accepting_states = {"s3"}
transition_function = {
    "s1": {
        "b" : "s1",
        "a" : "s2"
    },
    "s2": {
        "a" : "s2",
        "b" : "s1",
        "c" : "s3",
    },
    "s3":{
        "c" : "s3"
    }
}
dfa = SimpleDFA(states, alphabet, initial_state, accepting_states, transition_function)
Test word acceptance:
# a word is a list of symbols
word = "bbbac"
dfa.accepts(word)        # True

# without the last symbol c, the final state is not reached
dfa.accepts(word[:-1])   # False
Operations such as minimization and trimming:
dfa_minimized = dfa.minimize()
dfa_trimmed = dfa.trim()
Translate into a graphviz.Digraph instance:
graph = dfa.minimize().trim().to_graphviz()
To print the automaton:

graph.render("path_to_file")
For that you will need to install Graphviz. Please look at their download page for detailed instructions depending on your system.

The output looks like the following:



Features
Basic DFA and NFA support;
Algorithms for DFA minimization and trimming;
Algorithm for NFA determinization;
Translate automata into Graphviz objects.
Support for Symbolic Automata.
Tests
To run the tests:

tox
To run only the code style checks:

tox -e flake8 -e mypy
Docs
To build the docs:

mkdocs build
To view documentation in a browser

mkdocs serve
and then go to http://localhost:8000

License
Pythomata is released under the GNU Lesser General Public License v3.0 or later (LGPLv3+).

Copyright 2018-2020 WhiteMech


