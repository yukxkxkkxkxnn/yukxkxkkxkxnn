#include<vector>
#include <iostream>
#include<string>
#include<map>
using namespace std;
#define cehua 0
#define yanfa 1
#define zhixing 2
//创建人的属性放入vector容器中；
//给每个人分组，用时间定义工资和组
class person
{
public:
    person(string name, int salary)
    {
        this->m_name = name;
        this->m_salary = salary;
    }
    string m_name;
    int m_salary;
};
void  printall(multimap<int, person>&m)
{
    cout << "策划部门：" << endl;
    multimap<int, person>::iterator pos=m.find(cehua);
    int count = m.count(cehua);
    int a = 0;
    for (multimap<int, person>::iterator pos = m.find(cehua); pos != m.end() && a < count; pos++, a++)
    {
        cout << "姓名： " << (*pos).second.m_name<<"  工资：  "<<pos->second.m_salary << "     部门：  " << pos->first << endl;
    }
    cout << "研发部门：" << endl;
    multimap<int, person>::iterator pos2 = m.find(yanfa);
    int count2 = m.count(yanfa);
    int b = 0;
    for (multimap<int, person>::iterator pos2 = m.find(yanfa); pos2 != m.end() && b < count2; pos++, a++)
    {
        cout << "姓名： " << (*pos2).second.m_name <<"  工资：  " << pos2->second.m_salary << "     部门：  " << pos2->first << endl;
    }
    cout << "执行部门：" << endl;
    multimap<int, person>::iterator pos3 = m.find(zhixing);
    int count3 = m.count(zhixing);
    int c = 0;
    for (multimap<int, person>::iterator pos3 = m.find(zhixing); pos3 != m.end() && c < count3; pos3++, c++) {
        cout << "姓名： " << pos3->second.m_name << "  工资：  " << pos3->second.m_salary << "  部门：  " << pos3->first << endl;
    }
}
void print(vector<person>p)
{
    for (vector<person>::iterator it = p.begin(); it != p.end(); it++)
    {
        cout << (*it).m_name << "  " << (*it).m_salary << endl;
    }
    cout << endl;
}
void creattest01(vector<person>&p)
{
    string nameseed = "abcdefghij";
    for (int i = 0; i < 10; i++)
    {
        string name = "员工";
        name = name+nameseed[i];
        int salary = 0;
        salary = rand() % 10000 + 10000;
        person pn(name, salary);
        p.push_back(pn);
    }

}
void setgroup(vector<person>&p,multimap<int, person>&m)
{
    for (vector<person>::iterator it = p.begin(); it != p.end(); it++)
    {
        int dex = rand() % 3;
        m.insert(pair<int, person>(dex, *it));

    }
}
void test()
{
    vector<person>p;
    creattest01(p);
    print(p);//创建人和属性
    multimap<int, person>m;
    setgroup(p,m);
    printall(m);

}

int main()
{
    test();
}
  

