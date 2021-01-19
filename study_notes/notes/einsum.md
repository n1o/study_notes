# Einsum

![](../.images/einsum.png)

**If we repeated letters we want those axes multiplied together**

**If we omit a letter from the output it means that values along that axis will be summed over**
For 1D arrays
<table class="tg">
  <tbody><tr>
    <th class="tg-baqh"><b>Call signature</b></th>
    <th class="tg-baqh"><b>NumPy equivalent</b></th>
    <th class="tg-baqh"><b>Description</b></th>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('i', A)</code></td>
    <td class="tg-yw4l"><code>A</code></td>
    <td class="tg-yw4l">returns a view of A</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('i-&gt;', A)</code></td>
    <td class="tg-yw4l"><code>sum(A)</code></td>
    <td class="tg-yw4l">sums the values of A</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('i,i-&gt;i', A, B)</code></td>
    <td class="tg-yw4l"><code>A * B</code></td>
    <td class="tg-yw4l">element-wise multiplication of A and B</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('i,i', A, B)</code></td>
    <td class="tg-yw4l"><code>inner(A, B)</code></td>
    <td class="tg-yw4l">inner product of A and B</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('i,j-&gt;ij', A, B)</code></td>
    <td class="tg-yw4l"><code>outer(A, B)</code></td>
    <td class="tg-yw4l">outer product of A and B</td>
  </tr>
</tbody></table>

For matrices

<table class="tg">
  <tbody><tr>
    <th class="tg-031e"><b>Call signature</b></th>
    <th class="tg-031e"><b>NumPy equivalent</b></th>
    <th class="tg-031e"><b>Description</b></th>
  </tr>
  <tr>
    <td class="tg-031e"><code>('ij', A)</code></td>
    <td class="tg-031e"><code>A</code></td>
    <td class="tg-031e">returns a view of A</td>
  </tr>
  <tr>
    <td class="tg-031e"><code>('ji', A)</code></td>
    <td class="tg-031e"><code>A.T</code></td>
    <td class="tg-031e">view transpose of A</td>
  </tr>
  <tr>
    <td class="tg-031e"><code>('ii-&gt;i', A)</code></td>
    <td class="tg-031e"><code>diag(A)</code></td>
    <td class="tg-031e">view main diagonal of A</td>
  </tr>
  <tr>
    <td class="tg-031e"><code>('ii', A)</code></td>
    <td class="tg-031e"><code>trace(A)</code></td>
    <td class="tg-031e">sums main diagonal of A</td>
  </tr>
  <tr>
    <td class="tg-031e"><code>('ij-&gt;', A)</code></td>
    <td class="tg-031e"><code>sum(A)</code></td>
    <td class="tg-031e">sums the values of A</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij-&gt;j', A)</code></td>
    <td class="tg-yw4l"><code>sum(A, axis=0)</code></td>
    <td class="tg-yw4l">sum down the columns of A (across rows)</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij-&gt;i', A)</code></td>
    <td class="tg-yw4l"><code>sum(A, axis=1)</code></td>
    <td class="tg-yw4l">sum horizontally along the rows of A</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij,ij-&gt;ij', A, B)</code></td>
    <td class="tg-yw4l"><code>A * B</code></td>
    <td class="tg-yw4l">element-wise multiplication of A and B</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij,ji-&gt;ij', A, B)</code></td>
    <td class="tg-yw4l"><code>A * B.T</code></td>
    <td class="tg-yw4l">element-wise multiplication of A and B.T</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij,jk', A, B)</code></td>
    <td class="tg-yw4l"><code>dot(A, B)</code></td>
    <td class="tg-yw4l">matrix multiplication of A and B</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij,kj-&gt;ik', A, B)</code></td>
    <td class="tg-yw4l"><code>inner(A, B)</code></td>
    <td class="tg-yw4l">inner product of A and B</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij,kj-&gt;ikj', A, B)</code></td>
    <td class="tg-yw4l"><code>A[:, None] * B</code></td>
    <td class="tg-yw4l">each row of A multiplied by B</td>
  </tr>
  <tr>
    <td class="tg-yw4l"><code>('ij,kl-&gt;ijkl', A, B)</code></td>
    <td class="tg-yw4l"><code>A[:, :, None, None] * B</code></td>
    <td class="tg-yw4l">each value of A multiplied by B</td>
  </tr>
</tbody></table>

Ellipse syntax ```...```. This allows to nod index dimensions:

```
np.einsum('...ij,ji->...', a, b )
```

This multiplies the last wo axes of a with an 2d array b.