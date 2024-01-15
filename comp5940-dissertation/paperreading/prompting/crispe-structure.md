# CRISPE Structure

```
// bibtex reference
@misc{CRISPE,
    author = {{Matt Nigh}},
    year = {2023},
    title = {ChatGPT3 Prompt Engineering},
    howpublished = {\url{https://github.com/mattnigh/ChatGPT3-Free-Prompt-List}}    
}
```

## CRISPE Prompting Framework

是以下五种components的首字母组合而成，讲究prompt需要对问题与回复进行详细的定义。

{% tabs %}
{% tab title="中文" %}
能力与角色（Capacity and Role，CR）：LLM在其中扮演什么样的角色、希望LLM实现的功能？

背景（Insight，I）：对当前场景或问题背景的描述。

问题称述（Statement，S）：希望LLM实现的功能或回答的问题。

回答风格（Personality，P）：GPT回复的风格、格式或者语气等的限定。

实践要求（Experiment，E）：是否回复多个样例。
{% endtab %}

{% tab title="英文" %}
Capacity and Role: What role (or roles) should ChatGPT act as?&#x20;

Insight: Provides the behind the scenes insight, background, and context to your request.&#x20;

Statement: What you are asking ChatGPT to do.&#x20;

Personality: The style, personality, or manner you want ChatGPT to respond in.&#x20;

Experiment: Asking ChatGPT to provide multiple examples to you.
{% endtab %}
{% endtabs %}

<table><thead><tr><th width="155">Component</th><th>Examples</th></tr></thead><tbody><tr><td>CR</td><td>Act as an expert on software development on the topic of machine learning frameworks, and an expert blog writer.</td></tr><tr><td>I</td><td>The audience for this blog is technical professionals who are interested in learning about the latest advancements in machine learning.</td></tr><tr><td>S</td><td>Provide a comprehensive overview of the most popular machine learning frameworks, including their strengths and weaknesses. Include real-life examples and case studies to illustrate how these frameworks have been successfully used in various industries.</td></tr><tr><td>P</td><td>When responding, use a mix of the writing styles of Andrej Karpathy, Francois Chollet, Jeremy Howard, and Yann LeCun.</td></tr><tr><td>E</td><td>Give me multiple different examples.</td></tr><tr><td>Overall</td><td>Act as an expert on software development on the topic of machine learning frameworks, and an expert blog writer. The audience for this blog is technical professionals who are interested in learning about the latest advancements in machine learning. Provide a comprehensive overview of the most popular machine learning frameworks, including their strengths and weaknesses. Include real-life examples and case studies to illustrate how these frameworks have been successfully used in various industries. When responding, use a mix of the writing styles of Andrej Karpathy, Francois Chollet, Jeremy Howard, and Yann LeCun.</td></tr></tbody></table>

## Sample Prompt in Personality

{% tabs %}
{% tab title="中文" %}
`鼓励创造力`：“重写现有文档，使其更具想象力、吸引力和独特性。”\`&#x20;

`专注于讲故事`：“将现有文档转变为引人入胜的故事，突出所面临的挑战和提供的解决方案。”&#x20;

`使用有说服力的语言`：“通过结合有说服力的语言和技术来完善现有文件，使其更具说服力和影响力。”&#x20;

`强调情感`：“在现有文档中添加情感语言和感官细节，使其更具相关性和吸引力。”&#x20;

`利用感官细节`：“通过添加感官细节和描述性语言来完善现有文档，使其栩栩如生并吸引读者。”&#x20;

`使内容简洁`：“通过删除不必要的信息并使其更加简洁和切题来完善现有文档。”&#x20;

`突出要点`：“重写现有文档以强调要点并使其更具影响力。”&#x20;

`使用生动的语言`：“通过使用生动的语言和描述性形容词来完善现有文档，使其更具吸引力。”&#x20;

`营造紧迫感`：“通过增加紧迫感并强调立即采取行动的必要性来完善现有文件。”&#x20;

`解决异议`：“通过预测和解决对内容的潜在异议来完善现有文档。”&#x20;

`个性化内容`：“通过个性化语言并使其与读者更相关来完善现有文档。”

`使用清晰简洁的语言`：“用简单的术语解释技术概念。”&#x20;

`添加视觉辅助工具`：“使用 mermaid.js，您可以包含图表来说明复杂的概念（可靠性低）。”&#x20;

`使用标题和副标题`：“将文档划分为具有清晰标题和副标题的部分。”&#x20;

`突出显示要点`：“使用粗体或斜体文本强调重要信息。”&#x20;

`添加现实生活中的例子`：“包括案例研究或现实世界的例子，使概念更具有相关性。”&#x20;

`使用清晰一致的格式`：“在整个文档中使用一致的字体、字体大小和布局。”&#x20;

`包括类比和比较`：“使用类比或比较来解释复杂的想法。”&#x20;

`使用主动语态`：“用主动语态写作可以让句子更有吸引力、更容易理解。”
{% endtab %}

{% tab title="英文" %}
`Encourage creativity`: "Rewrite the existing document to make it more imaginative, engaging, and unique."&#x20;

`Focus on storytelling`: "Transform the existing document into a compelling story that highlights the challenges faced and the solutions provided."&#x20;

`Use persuasive language`: "Refine the existing document by incorporating persuasive language and techniques to make it more convincing and impactful."&#x20;

`Emphasize emotion`: "Add emotional language and sensory details to the existing document to make it more relatable and engaging."&#x20;

`Utilize sensory details`: "Refine the existing document by adding sensory details and descriptive language to bring it to life and engage the reader."&#x20;

`Make the content concise`: "Refine the existing document by removing unnecessary information and making it more concise and to-the-point."&#x20;

`Highlight key points`: "Rewrite the existing document to emphasize the key points and make them more impactful."&#x20;

`Use vivid language`: "Refine the existing document by using vivid language and descriptive adjectives to make it more engaging."&#x20;

`Create a sense of urgency`: "Refine the existing document by adding a sense of urgency and emphasizing the need for immediate action."&#x20;

`Address objections`: "Refine the existing document by anticipating and addressing potential objections to the content."&#x20;

`Personalize the content`: "Refine the existing document by personalizing the language and making it more relatable to the reader."

`Use clear and concise language`: "Explain technical concepts in simple terms."&#x20;

`Add visual aids`: "Using mermaid.js you can include diagrams to illustrate complex concepts (low reliability)."&#x20;

`Use headings and subheadings`: "Divide the document into sections with clear headings and subheadings."&#x20;

`Highlight key points`: "Emphasize important information using bold or italic text."&#x20;

`Add real-life examples`: "Include case studies or real-world examples to make concepts more relatable."&#x20;

`Use clear and consistent formatting`: "Use a consistent font, font size, and layout throughout the document."&#x20;

`Include analogies and comparisons`: "Explain complex ideas using analogies or comparisons."&#x20;

`Use active voice`: "Write in active voice to make sentences more engaging and easier to follow."
{% endtab %}
{% endtabs %}

