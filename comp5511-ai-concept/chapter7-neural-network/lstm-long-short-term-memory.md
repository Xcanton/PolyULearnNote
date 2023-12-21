# LSTM (Long Short Term Memory)

$$
\begin{pmatrix}
i \\
f \\
o \\
g
\end{pmatrix} = \begin{pmatrix}
sigm \\
sigm \\
sigm \\
tanh
\end{pmatrix}W^l\begin{pmatrix}
h_{t}^{l-1} \\
h_{t-1}^l
\end{pmatrix} \\c^l_t=f \cdot c_{t-1}^l + i \cdot g \\ h_t^l = o \cdot \tanh(c_t^l)
$$

