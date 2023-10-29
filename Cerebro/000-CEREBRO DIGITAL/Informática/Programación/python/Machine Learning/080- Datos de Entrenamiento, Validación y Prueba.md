---
ID: 80
tags: 
nombre: Datos de Entrenamiento, Validación y Prueba
---
___
# Datos de Entrenamiento, Validación y Prueba 
![](https://www.youtube.com/watch?v=vdYzm4xC7mc&ab_channel=C%C3%B3digoM%C3%A1quina)
## ¿Cómo crearlos y qué objetivos tienen?

- Los datos se dividen en tres conjuntos: entrenamiento, validación y prueba. Cada uno tiene un propósito diferente.
    
- Datos de entrenamiento: se utilizan para entrenar y ajustar el modelo. Es el conjunto más grande, típicamente 60-80% de los datos.
    
- Datos de validación: se utilizan para validar el modelo y ajustar hiperparámetros. Suele ser ~20% de los datos.
    
- Datos de prueba: se utilizan para probar el modelo entrenado. Evalúa la capacidad de generalización. ~20% de datos.
    
- Es importante que los conjuntos sean mutuamente excluyentes para evitar sesgos.
    
- Se recomienda una separación aleatoria de los datos en los conjuntos.
    
- Scikit-learn provee métodos para separar automáticamente los datos.
    

Puntos clave del video con tiempo:

- (00:42) Riesgo de sobreentrenamiento si se entrena y prueba con los mismos datos
- (02:53) El conjunto de entrenamiento es el más grande, para entrenar el modelo
- (04:19) El conjunto de prueba mide la generalización ante nuevos datos
- (07:07) El conjunto de validación permite ajuste de hiperparámetros
- (11:45) Recomendaciones para porcentajes de cada conjunto
- (13:20) Separación automática con Scikit-Learn


### Separación de Datos:
#### 60% Entrenamiento, 20% Validación, 20% Prueba

```python
import pandas as pd
from sklearn.model_selection import train_test_split
  
pacientes = pd.read_csv("problemas_del_corazon.csv")
pacientes
  
resto, prueba, resto_clase, prueba_clase = train_test_split(
    pacientes[["edad", "genero", "presion", "colesterol", "diabetico"]],
    pacientes["cardiaco"],
    test_size=0.20)
  
entrena, valida, entrena_clase, valida_clase = train_test_split(
    resto[["edad", "genero", "presion", "colesterol", "diabetico"]],
    resto_clase,
    test_size=0.25)
  
pacientes[pacientes["cardiaco"]==1]

```
<div>

<style scoped>

    .dataframe tbody tr th:only-of-type {

        vertical-align: middle;

    }

  

    .dataframe tbody tr th {

        vertical-align: top;

    }

  

    .dataframe thead th {

        text-align: right;

    }

</style>

<table border="1" class="dataframe">

  <thead>

    <tr style="text-align: right;">

      <th></th>

      <th>edad</th>

      <th>genero</th>

      <th>presion</th>

      <th>colesterol</th>

      <th>diabetico</th>

      <th>cardiaco</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <th>0</th>

      <td>53</td>

      <td>0</td>

      <td>128</td>

      <td>216</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>1</th>

      <td>53</td>

      <td>0</td>

      <td>138</td>

      <td>234</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>2</th>

      <td>51</td>

      <td>0</td>

      <td>130</td>

      <td>256</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>3</th>

      <td>66</td>

      <td>1</td>

      <td>120</td>

      <td>302</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>4</th>

      <td>62</td>

      <td>1</td>

      <td>130</td>

      <td>231</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>5</th>

      <td>44</td>

      <td>0</td>

      <td>108</td>

      <td>141</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>6</th>

      <td>63</td>

      <td>0</td>

      <td>135</td>

      <td>252</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>7</th>

      <td>52</td>

      <td>1</td>

      <td>134</td>

      <td>201</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>8</th>

      <td>48</td>

      <td>1</td>

      <td>122</td>

      <td>222</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>9</th>

      <td>45</td>

      <td>1</td>

      <td>115</td>

      <td>260</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>10</th>

      <td>34</td>

      <td>1</td>

      <td>118</td>

      <td>182</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>11</th>

      <td>57</td>

      <td>0</td>

      <td>128</td>

      <td>303</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>12</th>

      <td>71</td>

      <td>0</td>

      <td>110</td>

      <td>265</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>13</th>

      <td>54</td>

      <td>1</td>

      <td>108</td>

      <td>309</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>14</th>

      <td>52</td>

      <td>1</td>

      <td>118</td>

      <td>186</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>15</th>

      <td>41</td>

      <td>1</td>

      <td>135</td>

      <td>203</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>16</th>

      <td>58</td>

      <td>1</td>

      <td>140</td>

      <td>211</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>17</th>

      <td>35</td>

      <td>0</td>

      <td>138</td>

      <td>183</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>18</th>

      <td>51</td>

      <td>1</td>

      <td>100</td>

      <td>222</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>19</th>

      <td>45</td>

      <td>0</td>

      <td>130</td>

      <td>234</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>20</th>

      <td>44</td>

      <td>1</td>

      <td>120</td>

      <td>220</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>21</th>

      <td>62</td>

      <td>0</td>

      <td>124</td>

      <td>209</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>22</th>

      <td>54</td>

      <td>1</td>

      <td>120</td>

      <td>258</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>23</th>

      <td>51</td>

      <td>1</td>

      <td>94</td>

      <td>227</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>24</th>

      <td>29</td>

      <td>1</td>

      <td>130</td>

      <td>204</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>25</th>

      <td>51</td>

      <td>1</td>

      <td>140</td>

      <td>261</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>26</th>

      <td>43</td>

      <td>0</td>

      <td>122</td>

      <td>213</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>27</th>

      <td>55</td>

      <td>0</td>

      <td>135</td>

      <td>250</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>28</th>

      <td>51</td>

      <td>1</td>

      <td>125</td>

      <td>245</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>29</th>

      <td>59</td>

      <td>1</td>

      <td>140</td>

      <td>221</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>30</th>

      <td>52</td>

      <td>1</td>

      <td>128</td>

      <td>205</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>31</th>

      <td>58</td>

      <td>1</td>

      <td>105</td>

      <td>240</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>32</th>

      <td>41</td>

      <td>1</td>

      <td>112</td>

      <td>250</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>33</th>

      <td>45</td>

      <td>1</td>

      <td>128</td>

      <td>308</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>34</th>

      <td>60</td>

      <td>0</td>

      <td>102</td>

      <td>318</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>35</th>

      <td>52</td>

      <td>1</td>

      <td>152</td>

      <td>298</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>36</th>

      <td>42</td>

      <td>0</td>

      <td>102</td>

      <td>265</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>37</th>

      <td>67</td>

      <td>0</td>

      <td>115</td>

      <td>564</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>38</th>

      <td>68</td>

      <td>1</td>

      <td>118</td>

      <td>277</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>39</th>

      <td>46</td>

      <td>1</td>

      <td>101</td>

      <td>197</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>40</th>

      <td>54</td>

      <td>0</td>

      <td>110</td>

      <td>214</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>41</th>

      <td>58</td>

      <td>0</td>

      <td>100</td>

      <td>248</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>42</th>

      <td>48</td>

      <td>1</td>

      <td>124</td>

      <td>255</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>43</th>

      <td>57</td>

      <td>1</td>

      <td>132</td>

      <td>207</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>44</th>

      <td>52</td>

      <td>1</td>

      <td>138</td>

      <td>223</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>45</th>

      <td>54</td>

      <td>0</td>

      <td>132</td>

      <td>288</td>

      <td>1</td>

      <td>1</td>

    </tr>

    <tr>

      <th>46</th>

      <td>45</td>

      <td>0</td>

      <td>112</td>

      <td>160</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>47</th>

      <td>53</td>

      <td>1</td>

      <td>142</td>

      <td>226</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>48</th>

      <td>62</td>

      <td>0</td>

      <td>140</td>

      <td>394</td>

      <td>0</td>

      <td>1</td>

    </tr>

    <tr>

      <th>49</th>

      <td>52</td>

      <td>1</td>

      <td>108</td>

      <td>233</td>

      <td>1</td>

      <td>1</td>

    </tr>

  </tbody>

</table>

</div>

 
___

%%
tags: #pagmachine_learning #python   

Vínculos: [[000-Menú Machine Learning 📃|Menú Machine Learning 📃]] 
%%