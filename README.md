# SymMonDB

A database for lists of #l monomials of degree #d in #n variables up to the action of the symmetric group \( S_n \). \( S_n \) acts on the monomials by exchanging the variables.

It is unknown (to me) if it is possible to produce "efficiently" (in terms of speed and memory) such lists. In particular, I haven't found a way to write a Python iterator for this purpose. Such lists are really useful for computational purposes, particularly for testing statements about partition theory.

Having computed some myself, I'm adding them here. The codename for the lists is `f"deg{d}_var{n}_len{l}"`, and the extension is `.py` or `.pickle` depending on the encoding format: either as the explicit code of a dictionary in Python or as a compressed pickle file. The keys of the dictionaries are representative classes of the list of monomials up to the action of the symmetric group. The values represent the cardinality of the orbit of each representative.

As an example, here is the dictionary of 2 monomials of degree 4 in 2 variables up to the action of \( S_2 \). A monomial is represented by a tuple of exponents, so `(1, 3)` represents the monomial \( xy^3 \). The list of monomials is represented by a tuple of tuples, so `((1, 3), (0, 4))` represents the list \( (xy^3, y^4) \). Clearly, `(1, 3)` and `(3, 1)` are different monomials, while `((1, 3), (0, 4))` and `((0, 4), (1, 3))` represent the same list. (They are not stored as `frozenset` for memory efficiency.)

```python
deg4_var2_len2 = {
    ((1, 3), (0, 4)): 2,
    ((2, 2), (0, 4)): 2,
    ((3, 1), (0, 4)): 2,
    ((1, 3), (2, 2)): 2,
    ((4, 0), (0, 4)): 1,
    ((1, 3), (3, 1)): 1,
}
