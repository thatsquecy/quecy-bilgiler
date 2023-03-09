# Basit Örnek
Aşağıda basit bir C# örneği verilmiştir. Bu örnek, kullanıcının girdiği ismi bir Windows Form uygulaması aracılığıyla SQL Server veritabanına kaydediyor.

Öncelikle, Visual Studio'da yeni bir Windows Form uygulaması oluşturun ve formunuzda bir TextBox ve bir Button ekleyin. TextBox, kullanıcının ismini girmesi için kullanılacak ve Button ise ismi SQL Server veritabanına kaydetmek için kullanılacaktır.

Daha sonra, formunuzda bir SqlConnection bileşeni oluşturun ve bağlantı dizesini ayarlayın. Bu bağlantı dizesi, SQL Server veritabanının nerede bulunduğunu ve kullanıcı adı ve şifresini içermelidir.

Button'a tıklandığında, SqlConnection bileşenini kullanarak SqlCommand bileşeni oluşturun ve INSERT INTO sorgusunu kullanarak veritabanına kullanıcının girdiği ismi kaydedin.

Aşağıda örneği inceleyebilirsiniz:
```csharp
using System.Data.SqlClient;

private void buttonSave_Click(object sender, EventArgs e)
{
    // Kullanıcının girdiği ismi alın
    string name = textBoxName.Text;

    // SqlConnection bileşeni oluşturun ve bağlantı dizesini ayarlayın
    string connectionString = "Data Source=localhost;Initial Catalog=your_database_name;User ID=your_username;Password=your_password";
    SqlConnection connection = new SqlConnection(connectionString);

    // SqlCommand bileşeni oluşturun ve INSERT INTO sorgusunu kullanarak ismi veritabanına kaydedin
    string query = "INSERT INTO your_table_name (Name) VALUES (@Name)";
    SqlCommand command = new SqlCommand(query, connection);
    command.Parameters.AddWithValue("@Name", name);

    try
    {
        connection.Open();
        command.ExecuteNonQuery();
        MessageBox.Show("İsim veritabanına kaydedildi.");
    }
    catch (Exception ex)
    {
        MessageBox.Show("Veritabanına kaydedilirken bir hata oluştu: " + ex.Message);
    }
    finally
    {
        connection.Close();
    }
}
```
Bu örnek, kullanıcının girdiği ismi "your_table_name" adlı tabloya "Name" adlı sütuna kaydedecektir. "your_database_name" adlı veritabanında çalıştığınızdan emin olun ve "your_username" ve "your_password" değişkenlerini kendi veritabanı kimlik bilgilerinizle değiştirin.

Umarım bu örnek, Windows Form uygulamalarında SQL Server veritabanına kayıt işleminin nasıl yapıldığını anlamanıza yardımcı olur.
