# Serialise-to-file
Serialise to file

For example

`//Save`
`private void Form1_FormClosing(object sender, FormClosingEventArgs e)`
`{`
    `List<string> text = new List<string>();`
    `text.Add(textBox1.Text);`
    `text.Add(textBox2.Text);`
    `List<bool> trueFalse = new List<bool>();`
    `trueFalse.Add(checkBox1.Checked);`
    `trueFalse.Add(checkBox2.Checked);`
    `IFormData form = new FormData(text, trueFalse);`

    serializToFile.Serializ<IFormData>(form, "File.txt");
}

//Load
`private void Form1_Load(object sender, EventArgs e)`
`{`
    `IFormData formData = new FormData();`
    `formData = serializToFile.DeSerializ<IFormData>("File.txt");`


    if (formData == null) return;
    try
    {
        textBox1.Text = formData.TextboxText[0];
        textBox2.Text = formData.TextboxText[1];
        checkBox1.Checked = formData.Checkd[0];
        checkBox2.Checked = formData.Checkd[1];
    }
    catch (Exception ex)
    {
        MessageBox.Show(ex.Message);
    }
}
