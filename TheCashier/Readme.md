# The Cashier
aplikasi yang digunakan untuk perhitungan jumlah satu atau bisa lebih, barang dan jasa.

# Scope & Functionalities
- User dapat memasukkan Item
- User dapat memilih barang atau jasa
- User dapat memasukkan jumlah barang atau jasa
- User dapat menekan tombol "Tambahkan"

# How Does it Works ?
Diawali dari method MainWindow pada class MainWindow.xaml.cs kita mendeklarasikan:
```csharp
        public MainWindow()
        {
            InitializeComponent();
            calculator = new Calculator();
            listBox.ItemsSource = calculator.getListItem();
        }
```
dilanjutkan dengan perintah menambahkan barang 
```csharp
            private void AddButton_Click(object sender,
            RoutedEventArgs e)
```
kemudian terakhir perintah pemangilan item, penjumlahan, type yang dipilih, harga, total dari semua harga dan dilanjutkan penjumlahan
```csharp
        {
            string title = itemNameBox.Text;
            int quantity = int.Parse(quantityBox.Text);
            string type = typeBox.Text;    
            double price = double.Parse(priceBox.Text);
            Item item = new Item(new Random().Next(), title, quantity, type, price);
            calculator.addItem(item);
            double total = calculator.getTotal();
            totalLabel.Content = String.Format("Rp. {0}", total);
            listBox.Items.Refresh();
        }
```

# Prinsip single responsibility
```csharp
            private Calculator calculator;
``` 
dan 
```csharp
            private void AddButton_Click(object sender,
            RoutedEventArgs e)
```
karena bertanggung jawab pada setiap individu. dalam konteks pemrograman 