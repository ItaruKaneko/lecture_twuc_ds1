# 第8回
## ds_IIa_s1_and_2.md と一部共通
## slide05/17-


~~~~
x = c( 1.832, 1.777, 1.754, 1.791, 1.823, 2.066, 1.681, 1.806, 1.729, 1.958, 1.967, 1.915, 1.897, 2.175, 1.892 )
y = c( 1.64, 1.785, 1.527, 1.502, 1.502, 1.766, 1.505, 1.523, 1.52, 1.64, 1.588, 1.581, 1.511, 1.745, 1.598 )
z = c( "出雲国分寺", "上総国分寺", "百済廃寺", "興福寺（中）", "興福寺（東）", "相模国分寺", "信濃国分寺", "信濃国分尼寺", "下野国分寺", "唐招提寺", "東大寺", "遠江国分寺", "三河国分尼寺", "武蔵国分寺", "陸奥国分寺" )
data1 <- data.frame( 金堂の比 = x, 基壇の比 = y )
rownames(data1) <- z
#  金堂寸法比の95%信頼区間
mean(data1[, 1]) - 1.96 * sd(data1[, 1])
mean(data1[, 1]) + 1.96 * sd(data1[, 1])
#  基壇寸法比の95%信頼区間
mean(data1[, 2]) - 1.96 * sd(data1[, 2])
mean(data1[, 2]) + 1.96 * sd(data1[, 2])

~~~~



~~~~
data

reado

read.csv

vector




~~~~