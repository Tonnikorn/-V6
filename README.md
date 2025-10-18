document.getElementById('calculateBtn').addEventListener('click', function() {
    const priceSmall = 100;
    const priceLarge = 290;
    const priceBloom = 70;

    const small = parseFloat(document.getElementById('small').value) || 0;
    const large = parseFloat(document.getElementById('large').value) || 0;
    const bloom = parseFloat(document.getElementById('bloom').value) || 0;
    const tare = parseFloat(document.getElementById('tare').value) || 0;

    // น้ำหนักรวมก่อนหักตระกร้า
    let netSmall = small - tare;
    let netLarge = large - tare;
    let netBloom = bloom - tare;

    // ป้องกันน้ำหนักติดลบ
    netSmall = netSmall < 0 ? 0 : netSmall;
    netLarge = netLarge < 0 ? 0 : netLarge;
    netBloom = netBloom < 0 ? 0 : netBloom;

    const totalSmall = netSmall * priceSmall;
    const totalLarge = netLarge * priceLarge;
    const totalBloom = netBloom * priceBloom;
    const total = totalSmall + totalLarge + totalBloom;

    document.getElementById('total').innerHTML = `
        จี๋ใหญ่: ${totalLarge.toLocaleString()} บาท<br>
        จี๋เล็ก: ${totalSmall.toLocaleString()} บาท<br>
        เห็ดบาน: ${totalBloom.toLocaleString()} บาท<br>
        <strong>จำนวนเงินทั้งหมด: ${total.toLocaleString()} บาท</strong>
    `;

    // ล้างค่าตัวเลข
    document.getElementById('small').value = '';
    document.getElementById('large').value = '';
    document.getElementById('bloom').value = '';
    document.getElementById('tare').value = '';
});
