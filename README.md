# file_read_write
The repository is a example about how to use C++ to read and write a file(txt)

#include<iostream>
#include<fstream>
#include<string>

using namespace std;

int main()
{
//读取文件
	ifstream in;
	string filename="test.txt";
	//cin >> filename;

	in.open(filename);

	if (!in)
	{
		cerr << "can not open file!" << endl;
		return 1;
	}

	char ch[8]="freedom";
	char c;
	int count = 0;//计数变量
	int size = strlen(ch) - 1;
	int i;
	

	while (!in.eof())
	{
		in.read(&c, 1);
		if (c == ch[0])
		{
			for (i = 1; i < size; i++)
			{
				in.read(&c, 1);
				if (c != ch[i])
					break;
			}
			if (i == size)
				count++;
		}
	}

	in.close();

//写入文件
	char *path = "out.txt";
	ofstream fout(path);

	if (fout)
	{
		fout << "freedom 出现次数是: " <<count<< endl;
		fout.close();
	}

	return 0;
}
