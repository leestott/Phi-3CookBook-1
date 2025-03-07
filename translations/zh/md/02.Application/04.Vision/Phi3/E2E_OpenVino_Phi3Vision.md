此演示展示了如何使用预训练模型根据图像和文本提示生成Python代码。

[示例代码](../../../../../../code/06.E2E/E2E_OpenVino_Phi3-vision.ipynb)

以下是逐步说明：

1. **导入和设置**：
   - 导入所需的库和模块，包括用于图像处理的`requests`和`PIL`，以及用于处理模型和数据的`transformers`。

2. **加载和显示图像**：
   - 使用`PIL`库打开图像文件（`demo.png`）并显示。

3. **定义提示**：
   - 创建一条消息，其中包含图像以及生成用于处理图像并使用`plt`（matplotlib）保存的Python代码的请求。

4. **加载处理器**：
   - 从由`out_dir`目录指定的预训练模型中加载`AutoProcessor`。此处理器将处理文本和图像输入。

5. **创建提示**：
   - 使用`apply_chat_template`方法将消息格式化为适合模型的提示。

6. **处理输入**：
   - 将提示和图像处理为模型可以理解的张量。

7. **设置生成参数**：
   - 定义模型生成过程的参数，包括生成新tokens的最大数量以及是否对输出进行采样。

8. **生成代码**：
   - 模型根据输入和生成参数生成Python代码。使用`TextStreamer`处理输出，跳过提示和特殊tokens。

9. **输出**：
   - 打印生成的代码，该代码应包含用于处理图像并按照提示要求保存的Python代码。

此演示说明了如何使用OpenVino预训练模型，根据用户输入和图像动态生成代码。

**免责声明**：  
本文件通过基于机器的人工智能翻译服务翻译而成。尽管我们努力确保准确性，但请注意，自动翻译可能包含错误或不准确之处。应以原始语言的文件作为权威来源。对于关键信息，建议使用专业人工翻译。我们不对因使用此翻译而产生的任何误解或错误解释承担责任。