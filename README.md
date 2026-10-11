const updateClock = () => {
  const clockEl = document.getElementById('clock');
  if (!clockEl) return;

  const now = new Date();
  let hours = now.getHours();
  const minutes = String(now.getMinutes()).padStart(2, '0');
  const period = hours >= 12 ? 'PM' : 'AM';

  hours = hours % 12 || 12;
  clockEl.textContent = `${hours}:${minutes} ${period}`;
};

updateClock();
setInterval(updateClock, 30000);

const buttons = document.querySelectorAll('.nav-item, .quick-card, .control-btn');
buttons.forEach((button) => {
  button.addEventListener('click', () => {
    const group = button.classList.contains('nav-item') ? '.nav-item' :
      button.classList.contains('quick-card') ? '.quick-card' :
      '.control-btn';

    document.querySelectorAll(group).forEach((el) => el.classList.remove('active'));
    button.classList.add('active');
  });
});

const parkButton = document.querySelector('.park-btn');
parkButton?.addEventListener('click', () => {
  const isParked = parkButton.textContent.includes('PARKED');
  parkButton.textContent = isParked ? 'DRIVING' : 'PARKED';
  parkButton.style.color = isParked ? '#ffd166' : '#5ef0b4';
  parkButton.style.borderColor = isParked ? 'rgba(255, 209, 102, 0.7)' : 'rgba(75, 242, 185, 0.7)';
  parkButton.style.background = isParked
    ? 'linear-gradient(180deg, rgba(112, 90, 24, 0.35), rgba(40, 36, 24, 0.28))'
    : 'linear-gradient(180deg, rgba(17, 111, 90, 0.35), rgba(24, 51, 44, 0.28))';
});

const livePill = document.querySelector('.live-pill');
if (livePill) {
  setInterval(() => {
    livePill.style.opacity = livePill.style.opacity === '0.7' ? '1' : '0.7';
  }, 1200);
}
