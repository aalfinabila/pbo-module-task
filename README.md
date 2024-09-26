using System;
using System.Collections.Generic;

namespace TugasPR_PBO
{
    internal class Hewan
    {
        public string Nama;
        public int Umur;

        public Hewan(string nama, int umur)
        {
            Nama = nama;
            Umur = umur;
        }
        public virtual string Suara()
        {
            return "Hewan ini bersuara";
        }
        public virtual string InfoHewan()
        {
            return $"Nama: {Nama}, Umur: {Umur}";
        }
    }
    class Mamalia : Hewan
    {
        public int JumlahKaki;

        public Mamalia(string nama, int umur, int jumlahKaki) : base(nama, umur)
        {
            JumlahKaki = jumlahKaki;
        }

        public override string InfoHewan()
        {
            return base.InfoHewan() + $", Jumlah Kaki: {JumlahKaki}";
        }
    }

    class Reptil : Hewan
    {
        public double PanjangTubuh;

        public Reptil(string nama, int umur, double panjangTubuh) : base(nama, umur)
        {
            PanjangTubuh = panjangTubuh;
        }

        public override string InfoHewan()
        {
            return base.InfoHewan() + $", Panjang Tubuh: {PanjangTubuh} cm";
        }
    }

    class Singa : Mamalia
    {
        public Singa(string nama, int umur, int jumlahKaki) : base(nama, umur, jumlahKaki) { }

        public void Mengaum()
        {
            Console.WriteLine($"{Nama} sedang mengaum!");
        }

        public override string Suara()
        {
            return "RRRRRAWWWRRR";
        }
    }

    class Gajah : Mamalia
    {
        public Gajah(string nama, int umur, int jumlahKaki) : base(nama, umur, jumlahKaki) { }

        public override string Suara()
        {
            return "PPPWWWOOOHHH";
        }
    }

    class Ular : Reptil
    {
        public Ular(string nama, int umur, double panjangTubuh) : base(nama, umur, panjangTubuh) { }

        public void Merayap()
        {
            Console.WriteLine($"{Nama} sedang merayap.");
        }

        public override string Suara()
        {
            return "SSSSTTTT";
        }
    }

    class Buaya : Reptil
    {
        public Buaya(string nama, int umur, double panjangTubuh) : base(nama, umur, panjangTubuh) { }

        public override string Suara()
        {
            return "GGGGRRRRRR";
        }
    }

    class KebunBinatang
    {
        private List<Hewan> koleksiHewan = new List<Hewan>();

        public void TambahHewan(Hewan hewanBaru)
        {
            koleksiHewan.Add(hewanBaru);
        }

        public void DaftarHewan()
        {
            Console.WriteLine("Daftar Hewan");
            foreach (Hewan hewan in koleksiHewan)
            {
                Console.WriteLine(hewan.InfoHewan() + $", Suara: {hewan.Suara()}");
            }
        }
    }
    class Program
    {
        static void Main(string[] args)
        {
            KebunBinatang kebunBinatang = new KebunBinatang();

            Singa singa = new Singa("Leo", 7, 4);
            Gajah gajah = new Gajah("Jojo", 3, 4);
            Ular ular = new Ular("Aal", 5, 200);
            Buaya buaya = new Buaya("Coco", 2, 300);

            kebunBinatang.TambahHewan(singa);
            kebunBinatang.TambahHewan(gajah);
            kebunBinatang.TambahHewan(ular);
            kebunBinatang.TambahHewan(buaya);

            kebunBinatang.DaftarHewan();

        }
    }
}
