# CurrencyApps
Aplikasi ini adalah pengkonversian uang dollar (USD) ke Rupiah (IDR)

# Scope and Functionalities
Pengguna dapat menginputkan angka, button/tombol hitung, notifikasi tentang penginputan

# How Does it works?

        public MainWindow()
        {
            InitializeComponent();
            currencyController = new CurrencyController();
        }
Pada codingan di atas, inputan akan diproses jika memenuhi kriteria (angka). Berlanjut atau tidaknya proses berada pada line di atas

        private void hitungButton_Click(object sender, RoutedEventArgs e)
        {
            var nominalString = inputTextBox.Text;
            var result = "Inputan tidak valid";
            if(currencyController.isAllowed(nominalString))
            {
                result = "Rp. " + currencyController.usdToIdr(nominalString);
            }
            resultLabel.Content = result;
        }
Pada codingan di atas, akan berlanjut setelah melewati pemenuhan kriteria awal lalu berpindah pada ControllerCurrency.cs dan akan ditampilkan pada resultLabel.

        public string usdToIdr (string nominal)
        {
            var nominalDouble = Convert.ToDouble(nominal);
            var result = nominalDouble * 15000;
            return Convert.ToString(result);
        }
Codingan di atas adalah bagaimana logika proses dari pengkonversian IDR dari USD

        public Boolean isAllowed (string nominal)
        {
            Regex regex = new Regex("[^0-9.-]+");
            return !regex.IsMatch(nominal);
        }

#Latihan

1. Review kembali percobaan 1 sampai dengan 3 dengan menjawab pertanyaan-pertanyaan pada latihan tersebut.
        percobaan 1
        - angka hasil input dari InputTextBox sama dengan output dari resultLabel
        percobaan 2
        - angka hasil input dikalian 10000x dan di outputkan pada resultLabel
        Percobaan 3
        - jika inputan berisi angka maka akan dikalikan 4
        - jika salah inputan akan error 
        - jika menginputkan huruf maka value dan box rupiah akan menampilkan "Invalid"
2. Mengapa perlu membuat class CurrencyController.cs pada percobaan 4 ?
        mempermudah pembacaan bug atau eror dan meringkas suatu codingan
3. Jelaskan kegunaan method isAllowed pada percobaan 4!
        untuk menginialisasikan regex
4. Jelaskan secara singkat mengenai Regex pada percobaan 4!
        digunakan untuk menemukan karakter yang bukan angka
5. Buatlah class diagramnya pada percobaan 4!
        
