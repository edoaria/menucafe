
const menu = [
  {
    nama: "Es Kopi Susu",
    harga: 18000,
    kategori: "Minuman",
    tersedia: true,
    gambar: "images/kopi-susu.jpg"
  },
  {
    nama: "Nasi Goreng",
    harga: 25000,
    kategori: "Makanan",
    tersedia: true,
    gambar: "images/nasi-goreng.jpg"
  },
  {
    nama: "Chocolate Cake",
    harga: 22000,
    kategori: "Camilan",
    tersedia: false,
    gambar: "images/cokelat.jpg"
  }
];

const list = document.getElementById("menu-list");
const search = document.getElementById("search");
const emptyMessage = document.getElementById("empty-message");

let kategoriAktif = "Semua";

function renderMenu() {
  const keyword = search.value.toLowerCase();

  const hasil = menu.filter(item => {
    const cocokNama = item.nama.toLowerCase().includes(keyword);
    const cocokKategori =
      kategoriAktif === "Semua" ||
      item.kategori === kategoriAktif;

    return cocokNama && cocokKategori;
  });

  list.replaceChildren();

  hasil.forEach(item => {
    const card = document.createElement("article");
    card.className = "menu-card";

    const img = document.createElement("img");
    img.src = item.gambar;
    img.alt = item.nama;
    img.loading = "lazy";

    const info = document.createElement("div");
    info.className = "menu-info";

    const nama = document.createElement("h2");
    nama.textContent = item.nama;

    const harga = document.createElement("p");
    harga.className = "price";
    harga.textContent = "Rp" +
      item.harga.toLocaleString("id-ID");

    const status = document.createElement("p");
    status.className = item.tersedia
      ? "status"
      : "status habis";
    status.textContent = item.tersedia
      ? "Tersedia"
      : "Habis";

    info.append(nama, harga, status);
    card.append(img, info);
    list.append(card);
  });

  emptyMessage.hidden = hasil.length > 0;
}

search.addEventListener("input", renderMenu);

document.querySelectorAll("[data-category]").forEach(button => {
  button.addEventListener("click", () => {
    kategoriAktif = button.dataset.category;

    document.querySelectorAll("[data-category]")
      .forEach(item => item.classList.remove("active"));

    button.classList.add("active");
    renderMenu();
  });
});

document.querySelector('[data-category="Semua"]')
  .classList.add("active");

renderMenu();
