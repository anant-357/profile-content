# SNARK - Proof Of _Statement_

- has to be **fast** and **short**
  Zero Knowledge - reveals nothing about subject of _Statement_.

## Arithmetic Circuits - _C_

- DAG where
  - internal nodes are +, - or x
  - leaf nodes are 1, x<sub>1</sub>, x<sub>2</sub> ... x<sub>n</sub>
  - size of _C_ = number of internal nodes(+, -, x)

## Argument System

- Public Arithmetic Circuit C(_x_, _w_) <kbd>&rarr;</kbd> **_F_**
  - _x_ is a tuple of _n_ public statements
  - _w_ is a tuple of _m_ private witnesses
  - Two entities: **_Prover_** and **_Verifier_**
    - **_Prover_** convinces the **_Verifier_** that there exists some _w_ for which C(_x_, _w_) = 0
    - May require _Conversation_

### Preprocessing Argument Systems

- There is a preprocessing setup _S_ : S(_C_) <kbd>&rarr;</kbd> public parameters _(S<sub>p</sub>, S<sub>v</sub>)_
- **_Prover_** : P(S<sub>p</sub>, _x_, _w_) <kbd>&rarr;</kbd> proof <kbd>&#960;</kbd>
- **_Verifier_** : V(S<sub>v</sub>, _x_, _<kbd>&#960;</kbd>_) <kbd>&rarr;</kbd> **Accept** / **Reject**
- Removes the need of a _Conversation_. **_Prover_** sends proof _<kbd>&#960;</kbd>_ to **_Verifier_** who can only **Accept** or **Reject**

#### Requirements

- **Complete** : If **_Prover_** is honest, then the verifier _must_ **Accept**.
- **Knowledge Sound** : If **_Verifier_** **Accepts**, then **_Prover_** must know _w_ such that, C(_x_,_w_) = 0.
- **Zero Knowledge** (_Optional_) : (_C_, _S<sub>p</sub>_, _S<sub>v</sub>_, _x_, _<kbd>&#960;</kbd>_) reveal nothing about _w_

## SNARK - a **S**uccinct **AR**gument of **K**nowledge

- |<kbd>&#960;</kbd>| = _O(_**log(|C|)**, <kbd>K</kbd>_)_

- time(V) = _O(_ |_x_|, **log(|C|)**, <kbd>K</kbd>_)_
