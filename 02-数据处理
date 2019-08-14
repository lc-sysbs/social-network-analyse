## 数据预分析
# 持有机构总数,被持有总市值,被持有总比例
stock_sum,stock_value,stock_ratio = [],[],[] 
# 比例/机构数,调整比例/机构数,市值/机构数
ratio_sum,ratio_sum_,value_sum = [],[],[]
for i in range(len(data)):
    s,v,r,rs,vs = 0,0,0,0,0,0
    if data[i] != '':
        for j in range(len(data[i])):
            if data[i][j][-1] != '' :
                if float(data[i][j][-1]) >= 0.01:
                    s += 1
                    v += float(data[i][j][-3])
                    r += float(data[i][j][-1])
    if s != 0:
        rs = r/s
        vs = v/s
    stock_sum.append(s);stock_value.append(v);stock_ratio.append(r)
    ratio_sum.append(rs);value_sum.append(vs)
# ratio_sum.sort(reverse=True)
df0 = pd.DataFrame({'code':codes,'sum':stock_sum, 'value':stock_value, 'ratio':stock_ratio,
                    'ratio/sum':ratio_sum,'value/sum':value_sum})
path0 = 'C://Users//Administrator//Desktop//PC//ad_analyse.csv'
df0.to_csv(path0, index=False, sep=',')
## 筛选数据     
# 按机构持股比例
def filter_data(data,ratio):
    data1 = []
    for i in range(len(data)):
        d = []
        for j in range(len(data[i])):
            if data[i][j][-1] != '' :
                if float(data[i][j][-1]) >= ratio:
                    d.append(data[i][j])
        data1.append(d)
    return data1 
# 按持股市值筛选
def value_data(data,value):
    data1 = []
    for i in range(len(data)):
        d = []
        for j in range(len(data[i])):
            if data[i][j][10] != '' :
                if float(data[i][j][10]) >= value:
                    d.append(data[i][j])
        data1.append(d)
    return data1 
# 按机构类型筛选
def class_data(data,class_):
    data1 = []
    for i in range(len(data)):
        d = []
        for j in range(len(data[i])):
            if data[i][j][8] == class_:
                d.append(data[i][j])
        data1.append(d)
    return data1
# 筛选不同行业、概念指数股
path = 'C://Users//Administrator//Desktop//PC//hangye.csv'
df=pd.read_csv(path,error_bad_lines=False)  
code_ = []
code_ = list(df['code_fangdichan']) 
n = len(code_)
for i in range(n):
    if type(code_[-1]) == float:
        del code_[-1]
def cluster_data(data,code_):
    d = []
    for i in range(len(data)):
        if data[i] != []:
            if data[i][0][0] in code_:
                d.append(data[i])
    return d
# 运行筛选函数
data = filter_data(data,ratio)
data = value_data(data,value)
data = cluster_data(data,code_)
data = class_data(data,hold_class[0])
