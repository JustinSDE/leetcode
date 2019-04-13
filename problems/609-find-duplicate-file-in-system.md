# 609. Find Duplicate File in System | 在系统中查找重复文件

## Question description

<!--If you want to use the English description, use <p>Given a list of directory info including directory path, and all the files with contents in this directory, you need to find out all the groups of duplicate files in the file system in terms of their paths.</p>

<p>A group of duplicate files consists of at least <b>two</b> files that have exactly the same content.</p>

<p>A single directory info string in the <b>input</b> list has the following format:</p>

<p><code>&quot;root/d1/d2/.../dm f1.txt(f1_content) f2.txt(f2_content) ... fn.txt(fn_content)&quot;</code></p>

<p>It means there are <b>n</b> files (<code>f1.txt</code>, <code>f2.txt</code> ... <code>fn.txt</code> with content <code>f1_content</code>, <code>f2_content</code> ... <code>fn_content</code>, respectively) in directory <code>root/d1/d2/.../dm</code>. Note that n &gt;= 1 and m &gt;= 0. If m = 0, it means the directory is just the root directory.</p>

<p>The <b>output</b> is a list of group of duplicate file paths. For each group, it contains all the file paths of the files that have the same content. A file path is a string that has the following format:</p>

<p><code>&quot;directory_path/file_name.txt&quot;</code></p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b>
[&quot;root/a 1.txt(abcd) 2.txt(efgh)&quot;, &quot;root/c 3.txt(abcd)&quot;, &quot;root/c/d 4.txt(efgh)&quot;, &quot;root 4.txt(efgh)&quot;]
<b>Output:</b>  
[[&quot;root/a/2.txt&quot;,&quot;root/c/d/4.txt&quot;,&quot;root/4.txt&quot;],[&quot;root/a/1.txt&quot;,&quot;root/c/3.txt&quot;]]
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>No order is required for the final output.</li>
	<li>You may assume the directory name, file name and file content only has letters and digits, and the length of file content is in the range of [1,50].</li>
	<li>The number of files given is in the range of [1,20000].</li>
	<li>You may assume no files or directories share the same name in the same directory.</li>
	<li>You may assume each given directory info represents a unique directory. Directory path and file info are separated by a single blank space.</li>
</ol>

<p>&nbsp;</p>
<b>Follow-up beyond contest:</b>

<ol>
	<li>Imagine you are given a real file system, how will you search files? DFS or BFS?</li>
	<li>If the file content is very large (GB level), how will you modify your solution?</li>
	<li>If you can only read the file by 1kb each time, how will you modify your solution?</li>
	<li>What is the time complexity of your modified solution? What is the most time-consuming part and memory consuming part of it? How to optimize?</li>
	<li>How to make sure the duplicated files you find are not false positive?</li>
</ol>
 instead-->
<p>给定一个目录信息列表，包括目录路径，以及该目录中的所有包含内容的文件，您需要找到文件系统中的所有重复文件组的路径。一组重复的文件至少包括<strong>二个</strong>具有完全相同内容的文件。</p>

<p><strong>输入</strong>列表中的单个目录信息字符串的格式如下：</p>

<p><code>&quot;root/d1/d2/.../dm f1.txt(f1_content) f2.txt(f2_content) ... fn.txt(fn_content)&quot;</code></p>

<p>这意味着有 n 个文件（<code>f1.txt</code>,&nbsp;<code>f2.txt</code>&nbsp;...&nbsp;<code>fn.txt</code> 的内容分别是 <code>f1_content</code>,&nbsp;<code>f2_content</code>&nbsp;...&nbsp;<code>fn_content</code>）在目录&nbsp;<code>root/d1/d2/.../dm</code>&nbsp;下。注意：n&gt;=1 且 m&gt;=0。如果 m=0，则表示该目录是根目录。</p>

<p>该<strong>输出</strong>是重复文件路径组的列表。对于每个组，它包含具有相同内容的文件的所有文件路径。文件路径是具有下列格式的字符串：</p>

<p><code>&quot;directory_path/file_name.txt&quot;</code></p>

<p><strong>示例 1：</strong></p>

<pre><strong>输入：</strong>
[&quot;root/a 1.txt(abcd) 2.txt(efgh)&quot;, &quot;root/c 3.txt(abcd)&quot;, &quot;root/c/d 4.txt(efgh)&quot;, &quot;root 4.txt(efgh)&quot;]
<strong>输出：</strong>  
[[&quot;root/a/2.txt&quot;,&quot;root/c/d/4.txt&quot;,&quot;root/4.txt&quot;],[&quot;root/a/1.txt&quot;,&quot;root/c/3.txt&quot;]]
</pre>

<p>&nbsp;</p>

<p><strong>注：</strong></p>

<ol>
	<li>最终输出不需要顺序。</li>
	<li>您可以假设目录名、文件名和文件内容只有字母和数字，并且文件内容的长度在 [1，50] 的范围内。</li>
	<li>给定的文件数量在 [1，20000] 个范围内。</li>
	<li>您可以假设在同一目录中没有任何文件或目录共享相同的名称。</li>
	<li>您可以假设每个给定的目录信息代表一个唯一的目录。目录路径和文件信息用一个空格分隔。</li>
</ol>

<p>&nbsp;</p>

<p><strong>超越竞赛的后续行动：</strong></p>

<ol>
	<li>假设您有一个真正的文件系统，您将如何搜索文件？广度搜索还是宽度搜索？</li>
	<li>如果文件内容非常大（GB级别），您将如何修改您的解决方案？</li>
	<li>如果每次只能读取 1 kb 的文件，您将如何修改解决方案？</li>
	<li>修改后的解决方案的时间复杂度是多少？其中最耗时的部分和消耗内存的部分是什么？如何优化？</li>
	<li>如何确保您发现的重复文件不是误报？</li>
</ol>




## Solution

Language: **python3**  /  Runtime: 248 ms

```python3
class Solution:
    def findDuplicate(self, paths):
        """
        :type paths: List[str]
        :rtype: List[List[str]]
        """
        t = collections.defaultdict(list)
        for p in paths:
            d = p.split()[0]
            for _t in p.split()[1:]:
                f, c = _t[:-1].split('(')
                t[c].append(d+'/'+f)
        return [df for df in t.values() if len(df) > 1]

```



## Related Links

Question: [LeetCode](https://leetcode.com/problems/find-duplicate-file-in-system/description/)  /  [LeetCode中国](https://leetcode-cn.com/problems/find-duplicate-file-in-system/description/)

Solution: [LeetCode](https://leetcode.com/articles/find-duplicate-file-in-system/)  /  [LeetCode中国](https://leetcode-cn.com/articles/find-duplicate-file-in-system/)