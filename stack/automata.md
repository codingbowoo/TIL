기본 개념 정리

- States, Inputs, transitions
- The set of strings accepted by an automaton A : the language of A, L(A)
- Finite Automata and the languages they recognize
    - FAs are designed to :
        - *accept* some strings of symbols
        - *recognize* a language
    - FA is a machine covering all lengths (compared to circuits or decision trees)
    - Terminology& notations
        - Finite Alphabet of symbols
        - Word, length, empty string, concatenation
        - language L(A) : {w|w is accepted by a FA M}
    - FA consists of
        - Finite set of states
        - Finite set (alphabet) of input symbols
        - Lambda, the transition function
        - Start, Accepting state
    - Language L(A)
        - Is **regular** or **FA-recognizable** if it is recognized by some FA.
- Operations on languages: operations used to construct languages (from other ones)
    - Set operations: union, intersection, complement, set difference
    - Operations for sets of strings: concatenation, star
    - Among the operations above, **concatenation**, **star**, and **union** I are called as *Regular operat*i*ons*
    - FA-recognizable languages are closed under all six(union, intersection, complement, set diff, concat, star) operations
- Nondeterministic FAs
    - Add nondeterminism(allowing alternative computations on the same input string) to FAs to generalize
    - Add a guessing capability to FAs - How?
        - Allow δ(q, a) to specify more than one successor state
        - Add ε-transitions, transitions made for free , without consuming any input symbols
    - Languages NFAs recognizes: String w is *accepted* when there is at least one possible accepting end state
- (Deterministic) FAs vs. Nondeterministic FAs
    - DFAs are special cases of NFAs
    - NFAs recognizes at least the DFA-recognizable (regular) languages; If M is an NFA then L(M) is DFA-recognizable

(continue)
- Regular Expressions


이번 학기에 오토마타 조교를 하고 있는데 아무래도 기본기가 부족하다 <br>
내일 읽고 정리할 예정 <br>
[Automata, languages, and grammars](http://www.nature-of-computation.org/supplements/automata-notes.pdf) by Christopher Moore
