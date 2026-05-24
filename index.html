let savedReports = []; 
let currentRows = [];  
let activeCameraTarget = { rowIndex: null, type: null };
let streamInstance = null;

function resetTable() {
  document.getElementById('dynamic-rows').innerHTML = '';
  currentRows = [];
  addNewBlankRow(); 
}

function addNewBlankRow() {
  const index = currentRows.length;
  currentRows.push({ invNumber: '', photoInv: null, photoGen: null });
  
  const container = document.getElementById('dynamic-rows');
  const row = document.createElement('div');
  row.className = 'table-row';
  row.id = row-index-${index};
  row.innerHTML = `
    <div class="cell" style="color: #64748b;">${index + 1}</div>
    <div class="cell"><input type="text" class="cell-input" placeholder="Нажмите.." oninput="updateRowText(${index}, this.value)"></div>
    <div class="cell">
      <div class="cell-photo" id="p-inv-${index}" onclick="triggerCamera(${index}, 'inv')">
        <svg viewBox="0 0 24 24"><path d="M4 4h3l2-2h6l2 2h3c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2zm8 3c-2.76 0-5 2.24-5 5s2.24 5 5 5 5-2.24 5-5-2.24-5-5-5zm0 2c1.66 0 3 1.34 3 3s-1.34 3-3 3-3-1.34-3-3 1.34-3 3-3z"/></svg>
      </div>
    </div>
    <div class="cell">
      <div class="cell-photo" id="p-gen-${index}" onclick="triggerCamera(${index}, 'gen')">
        <svg viewBox="0 0 24 24"><path d="M4 4h3l2-2h6l2 2h3c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2zm8 3c-2.76 0-5 2.24-5 5s2.24 5 5 5 5-2.24 5-5-2.24-5-5-5zm0 2c1.66 0 3 1.34 3 3s-1.34 3-3 3-3-1.34-3-3 1.34-3 3-3z"/></svg>
      </div>
    </div>
  `;
  container.appendChild(row);
}

function openCreateScreen() {
  document.getElementById('screen-main').style.display = 'none';
  document.getElementById('screen-create').style.display = 'block';
  document.getElementById('report-type-select').value = 'Списание';
  resetTable();
}

function closeCreateScreen() {
  document.getElementById('screen-main').style.display = 'block';
  document.getElementById('screen-create').style.display = 'none';
}

function updateRowText(index, value) {
  currentRows[index].invNumber = value;
}

function saveCurrentReport() {
  const filledItems = currentRows.filter(r => r.invNumber || r.photoInv || r.photoGen);
  if (filledItems.length === 0) {
    alert("Нельзя сохранить пустой отчет. Заполните хотя бы одну строчку.");
    return;
  }

  const type = document.getElementById('report-type-select').value;
  const today = new Date().toLocaleDateString('ru-RU');
  
  const newReport = {
    id: Date.now(),
    type: type,
    count: filledItems.length,
    date: today,
    data: [...currentRows]
  };

  savedReports.unshift(newReport);
  renderReportsList();
  closeCreateScreen();
}

function renderReportsList() {
  const emptyBlock = document.getElementById('main-empty');
  const listBlock = document.getElementById('reports-list');

  if (savedReports.length === 0) {
    emptyBlock.style.display = 'flex';
    listBlock.style.display = 'none';
    return;
  }

  emptyBlock.style.display = 'none';
  listBlock.style.display = 'flex';
  listBlock.innerHTML = '';

  savedReports.forEach(rep => {
    const card = document.createElement('div');
    card.className = 'report-card';
    card.innerHTML = `
      <div class="report-info">
        <h3>${rep.type}</h3>
        <p>Количество ОС: ${rep.count}</p>
        <p>Дата: ${rep.date}</p>
      </div>
      <div class="report-card-actions">
        <button class="btn-icon" style="border-color: #10b981;" onclick="shareDirectReport(${rep.id})">
          <svg style="width:18px; height:18px; fill:#10b981;" viewBox="0 0 24 24"><path d="M18 16.08c-.76 0-1.44.3-1.96.77L8.91 12.7c.05-.23.09-.46.09-.7s-.04-.47-.09-.7l7.05-4.11c.54.5 1.25.81 2.04.81 1.66 0 3-1.34 3-3s-1.34-3-3-3-3 1.34-3 3c0 .24.04.47.09.7L8.04 9.81C7.5 9.31 6.79 9 6 9c-1.66 0-3 1.34-3 3s1.34 3 3 3c.79 0 1.5-.31 2.04-.81l7.12 4.16c-.05.21-.08.43-.08.65 0 1.61 1.31 2.92 2.92 2.92 1.61 0 2.92-1.31 2.92-2.92s-1.31-2.92-2.92-2.92z"/></svg>
        </button>
        <button class="btn-icon" style="border-color: var(--danger);" onclick="deleteReport(${rep.id})">
          <svg style="width:18px; height:18px; fill:var(--danger);" viewBox="0 0 24 24"><path d="M6 19c0 1.1.9 2 2 2h8c1.1 0 2-.9 2-2V7H6v12zM19 4h-3.5l-1-1h-5l-1 1H5v2h14V4z"/></svg>
        </button>
      </div>
    `;
    listBlock.appendChild(card);
  });
}

function deleteReport(id) {
  if (confirm("Удалить этот фотоотчет?")) {
    savedReports = savedReports.filter(r => r.id !== id);
    renderReportsList();
  }
}

async function triggerCamera(rowIndex, type) {
  activeCameraTarget = { rowIndex, type };
  const overlay = document.getElementById('camera-overlay');
  const frame = document.getElementById('scanner-frame-wrapper');
  
  frame.style.display = (type === 'inv') ? 'flex' : 'none';
  overlay.style.display = 'flex';

  try {
    streamInstance = await navigator.mediaDevices.getUserMedia({
      video: { facingMode: 'environment', width: { ideal: 1280 }, height: { ideal: 720 } },
      audio: false
    });
    document.getElementById('video-preview').srcObject = streamInstance;
  } catch (err) {
    alert("Камера недоступна. Открывайте по ссылке HTTPS.");
    stopCamera();
  }
}

function stopCamera() {
  if (streamInstance) {
    streamInstance.getTracks().forEach(t => t.stop());
  }
  document.getElementById('camera-overlay').style.display = 'none';
}

function takeSnapshot() {
  const video = document.getElementById('video-preview');
  const canvas = document.getElementById('hidden-canvas');
  const ctx = canvas.getContext('2d');

  canvas.width = video.videoWidth;
  canvas.height = video.videoHeight;
  ctx.drawImage(video, 0, 0, canvas.width, canvas.height);

  if (activeCameraTarget.type === 'inv') {
    const isSharp = evaluateSharpness(ctx, canvas.width, canvas.height);
    if (!isSharp) {
      if (!confirm("⚠️ Фотография размыта. Всё равно оставить её?")) {
        return;
      }
    }
  }

  const base64Img = canvas.toDataURL('image/jpeg', 0.55);
  const targetRow = currentRows[activeCameraTarget.rowIndex];
  
  if (activeCameraTarget.type === 'inv') targetRow.photoInv = base64Img;
  else targetRow.photoGen = base64Img;

  const elementId = p-${activeCameraTarget.type}-${activeCameraTarget.rowIndex};
  const element = document.getElementById(elementId);
  element.style.backgroundImage = url(${base64Img});
  element.classList.add('has-img');

  stopCamera();
}

function evaluateSharpness(ctx, w, h) {
  const size = 160;
  const x = Math.floor(w / 2 - size / 2);
  const y = Math.floor(h / 2 - size / 2);
  const data = ctx.getImageData(x, y, size, size).data;
  let diff = 0;
  for (let i = 0; i < data.length - 4; i += 4) {
    let v1 = (data[i] + data[i+1] + data[i+2]) / 3;
    let v2 = (data[i+4] + data[i+5] + data[i+6]) / 3;
    diff += Math.abs(v1 - v2);
  }
  return (diff / (size * size)) > 9.5;
}

function exportToExcel() {
  const items = currentRows.filter(r => r.invNumber || r.photoInv || r.photoGen);
  if (items.length === 0) {
    alert("Таблица пуста. Нечего отправлять.");
    return;
  }
  const type = document.getElementById('report-type-select').value;
  buildExcelAndShare(items, type);
}

function shareDirectReport(id) {
  const rep = savedReports.find(r => r.id === id);
  if (rep) {
    const items = rep.data.filter(r => r.invNumber || r.photoInv || r.photoGen);
    buildExcelAndShare(items, rep.type);
  }
}

async function buildExcelAndShare(validItems, typeName) {
  const workbook = new ExcelJS.Workbook();
  const worksheet = workbook.addWorksheet('Отчет ОС');

  worksheet.columns = [
    { header: '№ п/п', key: 'idx', width: 8 },
    { header: 'Инвентарный номер', key: 'invNum', width: 25 },
    { header: 'Фото инвентарного номера', key: 'imgInv', width: 35 },
    { header: 'Общий вид ОС', key: 'imgGen', width: 35 }
  ];

  const hRow = worksheet.getRow(1);
  hRow.height = 28;
  hRow.eachCell((c) => {
    c.font = { name: 'Arial', size: 11, bold: true };
    c.fill = { type: 'pattern', pattern: 'solid', fgColor: { argb: 'FFEAEAEA' } };
    c.alignment = { vertical: 'middle', horizontal: 'center', wrapText: true };
    c.border = { top: {style:'thin'}, left: {style:'thin'}, bottom: {style:'medium'}, right: {style:'thin'} };
  });

  for (let i = 0; i < validItems.length; i++) {
    const item = validItems[i];
    const rNum = i + 2;
    const r = worksheet.getRow(rNum);
    
    r.getCell(1).value = i + 1; 
    r.getCell(2).value = item.invNumber || '';
    r.height = 110;

    r.getCell(1).alignment = { vertical: 'middle', horizontal: 'center' };
    r.getCell(2).alignment = { vertical: 'middle', horizontal: 'center', font: { size: 12, bold: true } };

    for(let col=1; col<=4; col++) {
      r.getCell(col).border = { top: {style:'thin'}, left: {style:'thin'}, bottom: {style:'thin'}, right: {style:'thin'} };
    }

    if (item.photoInv) {
      const imgId = workbook.addImage({ base64: item.photoInv, extension: 'jpeg' });
      worksheet.addImage(imgId, { tl: { col: 2.1, row: rNum - 0.9 }, ext: { width: 230, height: 130 } });
    }
    if (item.photoGen) {
      const imgId = workbook.addImage({ base64: item.photoGen, extension: 'jpeg' });
      worksheet.addImage(imgId, { tl: { col: 3.1, row: rNum - 0.9 }, ext: { width: 230, height: 130 } });
    }
  }

  const buffer = await workbook.xlsx.writeBuffer();
  const blob = new Blob([buffer], { type: 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet' });
  const fName = ${typeName}_OS_${new Date().toISOString().slice(0,10)}.xlsx;
  const file = new File([blob], fName, { type: blob.type });

  if (navigator.canShare && navigator.canShare({ files: [file] })) {
    try {
      await navigator.share({ files: [file], title: Фотоотчет: ${typeName} });
    } catch (err) {
      if (err.name !== "AbortError") alert("Ошибка отправки: " + err.message);
    }
  } else {
    const link = document.createElement('a');
    link.href = URL.createObjectURL(blob);
    link.download = fName;
    link.click();
    alert("Файл скачан на устройство в папку Загрузки.");
  }
}
