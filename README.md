package com.juaracoding;

import java.util.ArrayList;
import java.util.Scanner;

public class Pratikum {
    public static void main(String[] args) {
        System.out.println("=== Login ===");

        String username = "admin";
        String password = "12345";

        Scanner scanner = new Scanner(System.in);
        System.out.print("Username: ");
        String inUsername = scanner.nextLine();
        System.out.print("Password: ");
        String inPassword = scanner.nextLine();

        if (username.equals(inUsername) && password.equals(inPassword)) {
            System.out.println("Login Berhasil");

            ArrayList<String> daftarFilm = new ArrayList<>();

            int pilihan;
            do {

                System.out.println("\n=== Menu Utama ===");
                System.out.println("1. Tampilkan Daftar Film");
                System.out.println("2. Input Data Film");
                System.out.println("3. Cari Film");
                System.out.println("4. Keluar");
                System.out.print("Pilih: ");

                pilihan = scanner.nextInt();
                scanner.nextLine();

                switch (pilihan) {
                    case 1:
                        System.out.println("\n=== Daftar Film ===");
                        if (daftarFilm.isEmpty()) {
                            System.out.println("Belum ada film.");
                        } else {
                            for (int i = 0; i < daftarFilm.size(); i++) {
                                System.out.println((i + 1) + ". " + daftarFilm.get(i));
                            }
                        }
                        break;

                    case 2:
                        int sisaSlot = 10 - daftarFilm.size();
                        if (sisaSlot == 0) {
                            System.out.println("Maaf, daftar film sudah penuh (maksimal 10 film).");
                        } else {
                            System.out.print("Berapa banyak film yang ingin ditambahkan (maks " + sisaSlot + ")? ");
                            int jumlah = scanner.nextInt();
                            scanner.nextLine(); // buang newline

                            if (jumlah <= 0 || jumlah > sisaSlot) {
                                System.out.println("Jumlah tidak valid. Maksimal: " + sisaSlot);
                            } else {
                                for (int i = 1; i <= jumlah; i++) {
                                    System.out.print("Masukkan judul film ke-" + i + ": ");
                                    String filmBaru = scanner.nextLine();
                                    if (!filmBaru.isBlank()) {
                                        daftarFilm.add(filmBaru);
                                        System.out.println("✔ Film '" + filmBaru + "' ditambahkan.");
                                    } else {
                                        System.out.println("❌ Judul kosong, film tidak ditambahkan.");
                                        i--; // ulangi input
                                    }
                                }
                            }
                        }
                        break;

                    case 3:
                        System.out.print("Masukkan judul film yang ingin dicari: ");
                        String keyword = scanner.nextLine().toLowerCase();
                        boolean ditemukan = false;
                        for (String f : daftarFilm) {
                            if (f.toLowerCase().contains(keyword)) {
                                System.out.println("Ditemukan: " + f);
                                ditemukan = true;
                            }
                        }
                        if (!ditemukan) {
                            System.out.println("Film tidak tersedia");
                        }
                        break;

                    case 4:
                        System.out.println("Terima kasih!");
                        break;

                    default:
                        System.out.println("Pilihan tidak valid.");
                }

            } while (pilihan != 4);

        } else {
            System.out.println("Login gagal!");
        }

        scanner.close();
    }
}
