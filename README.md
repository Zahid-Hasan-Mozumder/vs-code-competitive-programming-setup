# vs-code-competitive-programming-setup

A simple setup for C++ and Java competitive programming with automated testing.

## 📁 Folder Structure

```
competitive-programming/
├── cpp/
│   ├── sol.cpp
│   ├── input.txt
│   ├── output.txt
│   └── .vscode/tasks.json
└── java/
    ├── sol.java
    ├── input.txt
    ├── output.txt
    └── .vscode/tasks.json
```

## 🚀 Setup

### Prerequisites

**For C++:**
- Install MinGW-w64 (Windows) or GCC
- Install **C/C++ Extension** in VS Code

**For Java:**
- Install JDK 8+
- Install **Extension Pack for Java** in VS Code

### Installation

1. Create the folder structure above
2. Open `cpp` or `java` folder in VS Code
3. Create `.vscode/tasks.json` with the config below
4. Install the required extension

## ⚙️ Configuration

### C++ (`cpp/.vscode/tasks.json`)

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "compile and run",
            "type": "shell",
            "command": "g++ -std=c++17 -o \"${fileBasenameNoExtension}.exe\" \"${file}\" && \"${fileBasenameNoExtension}.exe\" < input.txt > output.txt",
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "options": {
                "shell": {
                    "executable": "cmd.exe",
                    "args": ["/d", "/c"]
                }
            }
        }
    ]
}
```

### Java (`java/.vscode/tasks.json`)

```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "compile and run",
            "type": "shell",
            "command": "cmd.exe",
            "args": [
                "/d",
                "/c",
                "javac \"${file}\" && java -cp \"${fileDirname}\" \"${fileBasenameNoExtension}\" < input.txt > output.txt"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "options": {
                "shell": {
                    "executable": "cmd.exe",
                    "args": ["/d", "/c"]
                }
            }
        }
    ]
}
```

## 💻 Usage

1. Write your code in `sol.cpp` or `sol.java`
2. Add test cases in `input.txt`
3. Press **`Ctrl+Shift+B`**
4. Check output in `output.txt`

## 📝 Templates

### C++ Template

```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    cout.tie(NULL);
    
    int t; cin >> t;
    while(t--) {
        // Your code here
    }
}
```

### Java Template

```java
import java.io.*;
import java.util.*;

public class sol {

    static FastReader in = new FastReader();
    static PrintWriter out = new PrintWriter(System.out);

    public static void main(String[] args) {
        int t = in.nextInt();
        while (t-- > 0) {
            /*
            Your code here
            
            int n = in.nextInt();
            int ans = 0;
            for (int i = 0; i < n; i++) {
                int cur = in.nextInt();
                ans += cur;
            }
            out.println(ans);
            */
        }
        out.close();
    }

    // FastReader class for fast i/o ----------------------------------------------
    static class FastReader {

        BufferedReader br;
        StringTokenizer st;

        public FastReader() {
            br = new BufferedReader(new InputStreamReader(System.in));
        }

        String next() {
            while (st == null || !st.hasMoreElements()) {
                try {
                    st = new StringTokenizer(br.readLine());
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
            return st.nextToken();
        }

        int nextInt() {
            return Integer.parseInt(next());
        }

        long nextLong() {
            return Long.parseLong(next());
        }

        double nextDouble() {
            return Double.parseDouble(next());
        }

        String nextLine() {
            String str = "";
            try {
                str = br.readLine();
            } catch (IOException e) {
                e.printStackTrace();
            }
            return str;
        }

        int[] nextIntArray(int n) {
            int[] arr = new int[n];
            for (int i = 0; i < n; i++) {
                arr[i] = nextInt();
            }
            return arr;
        }

        long[] nextLongArray(int n) {
            long[] arr = new long[n];
            for (int i = 0; i < n; i++) {
                arr[i] = nextLong();
            }
            return arr;
        }
    }
}
```

## 🐛 Troubleshooting

**"g++ is not recognized"**
- Add MinGW `bin` folder to system PATH
- Verify: `g++ --version`

**"javac is not recognized"**
- Add JDK `bin` folder to system PATH
- Verify: `javac -version`

**Output not updating**
- Check for compilation errors
- Ensure `input.txt` exists
- Close `output.txt` if open

---

**Happy Coding! 🚀**

