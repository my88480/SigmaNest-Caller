# SigmaNest-Caller

This project is the top secret project of my company. Let us wait for the project's Decryption.

C#

	string extensionFilename;
	DialogResult result;
	String fileName = null;
	String PartName = null;

	result = 0;

	if (fileName == null)
	{
		OpenFileDialog openFileDialog1 = new OpenFileDialog();
		openFileDialog1.Filter = "DXF文件(*.dxf)|*.dxf|所有文件(*.*)|*.*";
		openFileDialog1.InitialDirectory = "C:\\Users\\Public\\Documents\\SNDATA\\DXF\\";//注意这里写路径时要用c:\\而不是c:\
		openFileDialog1.DefaultExt = "dxf";//默认的文件扩展名
		result = openFileDialog1.ShowDialog();
		if (result == DialogResult.OK)
		{
			PartName = openFileDialog1.SafeFileName.Split(new string[] { "." }, StringSplitOptions.None)[0];
			fileName = openFileDialog1.FileName;
		}
	}
	if (result == DialogResult.OK || fileName != null)
	{
		extensionFilename = fileName.Substring(fileName.LastIndexOf(".") + 1);
		extensionFilename = extensionFilename.ToLower();
		//MessageBox.Show(extensionFilename);
		//MainRichTextBox.LoadFile(fName, RichTextBoxStreamType.UnicodePlainText);
		ISNPartObj isnPartObj = sa.PartExportImport.ImportPart2(ImportID.iiDXF, fileName);
		isnPartObj.QtyToNest = 20;
		isnPartObj.Thickness = 36;
		isnPartObj.Material = "16MnDR";
		isnPartObj.Name = PartName;
		sa.PartTile();
		sa.Redraw();
	}


https://www.sigmanest.com/

SigmaNEST nesting software is the world's leading nesting solution for all fabrication machines.

SigmaNEST is simply the best nesting software in the industry. Developed and supported by an expert team of mathematicians and engineers, SigmaNEST offers unparalleled material utilization and nesting efficiency. With unmatched versatility and maximum scalability, you can be confident in SigmaNEST’s abilities to meet your requirements, from quote to delivery and beyond.
