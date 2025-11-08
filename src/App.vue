<script setup>
import { ref, onMounted } from 'vue'

const STORAGE_KEY = 'wordsToGo'

const words = ref([{ word: 'a ajuta', clip: 'a-ajuta.mp4' }, { word: 'a alege', clip: 'a-alege.mp4' }, { word: 'a arăta', clip: 'a-arata.mp4' }, { word: 'a cere', clip: 'a-cere.mp4' }, { word: 'a deschide', clip: 'a-deschide.mp4' }, { word: 'a face', clip: 'a-face.mp4' }, { word: 'a găsi', clip: 'a-gasi.mp4' }, { word: 'a lucra', clip: 'a-lucra.mp4' }, { word: 'a merge', clip: 'a-merge.mp4' }, { word: 'a oferi', clip: 'a-oferi.mp4' }, { word: 'a plăti', clip: 'a-plati.mp4' }, { word: 'a pune', clip: 'a-pune.mp4' }, { word: 'a repara', clip: 'a-repara.mp4' }, { word: 'a ridica', clip: 'a-ridica.mp4' }, { word: 'a ruga', clip: 'a-ruga.mp4' }, { word: 'a răspunde', clip: 'a-raspunde.mp4' }, { word: 'a spăla', clip: 'a-spala.mp4' }, { word: 'a sta', clip: 'a-sta.mp4' }, { word: 'a vinde', clip: 'a-vinde.mp4' }, { word: 'a împacheta', clip: 'a-impacheta.mp4' }, { word: 'a împinge', clip: 'a-impinge.mp4' }, { word: 'a începe', clip: 'a-incepe.mp4' }, { word: 'a încerca', clip: 'a-incerca.mp4' }, { word: 'a închide', clip: 'a-inchide.mp4' }, { word: 'a învăța', clip: 'a-invata.mp4' }, { word: 'acasă', clip: 'acasa.mp4' }, { word: 'acoperiș', clip: 'acoperis.mp4' }, { word: 'aici', clip: 'aici.mp4' }, { word: 'alb', clip: 'alb.mp4' }, { word: 'albastru', clip: 'albastru.mp4' }, { word: 'aproape', clip: 'aproape.mp4' }, { word: 'aragaz', clip: 'aragaz.mp4' }, { word: 'aur', clip: 'aur.mp4' }, { word: 'autobuz', clip: 'autobuz.mp4' }, { word: 'avion', clip: 'avion.mp4' }, { word: 'azi', clip: 'azi.mp4' }, { word: 'ață', clip: 'ata.mp4' }, { word: 'bagaj', clip: 'bagaj.mp4' }, { word: 'bani', clip: 'bani.mp4' }, { word: 'bec', clip: 'bec.mp4' }, { word: 'birou', clip: 'birou.mp4' }, { word: 'bloc', clip: 'bloc.mp4' }, { word: 'bună ziua', clip: 'buna-ziua.mp4' }, { word: 'cablu tv', clip: 'cablu-tv.mp4' }, { word: 'cadă', clip: 'cada.mp4' }, { word: 'calculator', clip: 'calculator.mp4' }, { word: 'calorifer', clip: 'calorifer.mp4' }, { word: 'cameră', clip: 'camera.mp4' }, { word: 'canapea', clip: 'canapea.mp4' }, { word: 'cap', clip: 'cap.mp4' }, { word: 'card', clip: 'card.mp4' }, { word: 'carne', clip: 'carne.mp4' }, { word: 'carte', clip: 'carte.mp4' }, { word: 'casier', clip: 'casier.mp4' }, { word: 'casă', clip: 'casa.mp4' }, { word: 'ce', clip: 'ce.mp4' }, { word: 'cheie', clip: 'cheie.mp4' }, { word: 'chibrit', clip: 'chibrit.mp4' }, { word: 'coajă', clip: 'coaja.mp4' }, { word: 'cum', clip: 'cum.mp4' }, { word: 'cum te pot ajuta', clip: 'cum-te-pot-ajuta.mp4' }, { word: 'cumpărături', clip: 'comparaturi.mp4' }, { word: 'cuțit', clip: 'cutit.mp4' }, { word: 'da', clip: 'da.mp4' }, { word: 'defect', clip: 'defect.mp4' }, { word: 'degete', clip: 'degete.mp4' }, { word: 'desen', clip: 'desen.mp4' }, { word: 'devreme', clip: 'devreme.mp4' }, { word: 'din', clip: 'din.mp4' }, { word: 'director', clip: 'director.mp4' }, { word: 'discount (reducere)', clip: 'discount.mp4' }, { word: 'dreapta', clip: 'dreapta.mp4' }, { word: 'drum', clip: 'drum.mp4' }, { word: 'dulap', clip: 'dulap.mp4' }, { word: 'electrician', clip: 'electrician.mp4' }, { word: 'este', clip: 'este.mp4' }, { word: 'eu', clip: 'eu.mp4' }, { word: 'fier', clip: 'fier.mp4' }, { word: 'firmă', clip: 'firma.mp4' }, { word: 'foc', clip: 'foc.mp4' }, { word: 'fotografie', clip: 'fotografie.mp4' }, { word: 'frumos', clip: 'frumos.mp4' }, { word: 'fular', clip: 'fular.mp4' }, { word: 'fântână', clip: 'fantana.mp4' }, { word: 'garanție', clip: 'garantie.mp4' }, { word: 'gaz', clip: 'gaz.mp4' }, { word: 'greșeală', clip: 'greseala.mp4' }, { word: 'greșit', clip: 'gresit.mp4' }, { word: 'grup', clip: 'grup.mp4' }, { word: 'gunoi', clip: 'gunoi.mp4' }, { word: 'găsim o soluție împreună!', clip: 'gasim-o-solutie-impreuna.mp4' }, { word: 'halat', clip: 'halat.mp4' }, { word: 'hotel', clip: 'hotel.mp4' }, { word: 'ieftin', clip: 'ieftin.mp4' }, { word: 'imprimantă', clip: 'imprimanta.mp4' }, { word: 'inginer', clip: 'inginer.mp4' }, { word: 'inimă', clip: 'inima.mp4' }, { word: 'interfon', clip: 'interfon.mp4' }, { word: 'internet', clip: 'internet.mp4' }, { word: 'la', clip: 'la.mp4' }, { word: 'lampă', clip: 'lampa.mp4' }, { word: 'lemn', clip: 'lemn.mp4' }, { word: 'lumină', clip: 'lumina.mp4' }, { word: 'lună (calendar)', clip: 'luna-calendar.mp4' }, { word: 'magazin', clip: 'magazin.mp4' }, { word: 'magazin ieftin', clip: 'magazin-ieftin.mp4' }, { word: 'mașină', clip: 'masina.mp4' }, { word: 'muncitor', clip: 'muncitor.mp4' }, { word: 'muncă', clip: 'munca.mp4' }, { word: 'mână', clip: 'mana.mp4' }, { word: 'mănuși', clip: 'manusi.mp4' }, { word: 'nu', clip: 'nu.mp4' }, { word: 'nu este o problemă', clip: 'nu-este-o-problema.mp4' }, { word: 'nu mă interesează', clip: 'nu-ma-intereseaza.mp4' }, { word: 'nu mă simt bine', clip: 'nu-ma-simt-bine.mp4' }, { word: 'numele meu este', clip: 'numele-meu-este.mp4' }, { word: 'ok', clip: 'ok.mp4' }, { word: 'om', clip: 'om.mp4' }, { word: 'parcare', clip: 'parcare.mp4' }, { word: 'parchet', clip: 'parchet.mp4' }, { word: 'perete', clip: 'perete.mp4' }, { word: 'perfect', clip: 'perfect.mp4' }, { word: 'perie', clip: 'perie.mp4' }, { word: 'perioadă', clip: 'perioada.mp4' }, { word: 'picior', clip: 'picior.mp4' }, { word: 'pierdut', clip: 'pierdut.mp4' }, { word: 'plasă', clip: 'plasa.mp4' }, { word: 'plecări', clip: 'plecari.mp4' }, { word: 'poartă', clip: 'poarta.mp4' }, { word: 'pod', clip: 'pod.mp4' }, { word: 'podea', clip: 'podea.mp4' }, { word: 'posibilitate', clip: 'posibilitate.mp4' }, { word: 'poză (fotografie)', clip: 'poza-fotografie.mp4' }, { word: 'preț', clip: 'pret.mp4' }, { word: 'problemă', clip: 'problema.mp4' }, { word: 'program', clip: 'program.mp4' }, { word: 'prosop', clip: 'prosop.mp4' }, { word: 'pungă', clip: 'punga.mp4' }, { word: 'puternic', clip: 'puternic.mp4' }, { word: 'puțin', clip: 'putin.mp4' }, { word: 'pământ', clip: 'pamant.mp4' }, { word: 'păr', clip: 'par.mp4' }, { word: 'reclamație', clip: 'reclamatie.mp4' }, { word: 'reducere', clip: 'reducere.mp4' }, { word: 'repede', clip: 'repede.mp4' }, { word: 'respect', clip: 'respect.mp4' }, { word: 'rucsac', clip: 'rucsac.mp4' }, { word: 'răbdare', clip: 'rabdare.mp4' }, { word: 'răspunde', clip: 'raspunde.mp4' }, { word: 'salut', clip: 'salut.mp4' }, { word: 'scară', clip: 'scara.mp4' }, { word: 'scaun', clip: 'scaun.mp4' }, { word: 'scump', clip: 'scump.mp4' }, { word: 'scuze', clip: 'scuze.mp4' }, { word: 'semn', clip: 'semn.mp4' }, { word: 'sertar', clip: 'sertar.mp4' }, { word: 'sfat', clip: 'sfat.mp4' }, { word: 'singur', clip: 'singur.mp4' }, { word: 'societate', clip: 'societate.mp4' }, { word: 'sprijin', clip: 'sprijin.mp4' }, { word: 'sticlă', clip: 'sticla.mp4' }, { word: 'stop', clip: 'stop.mp4' }, { word: 'stradă', clip: 'strada.mp4' }, { word: 'stânga', clip: 'stanga.mp4' }, { word: 'sub', clip: 'sub.mp4' }, { word: 'sufragerie', clip: 'sufragerie.mp4' }, { word: 'sumă', clip: 'suma.mp4' }, { word: 'sunt', clip: 'sunt.mp4' }, { word: 'sunt bine', clip: 'sunt-bine.mp4' }, { word: 'sunt din bucurești', clip: 'sunt-din-bucuresti.mp4' }, { word: 'sunt hipoacuzic/ă', clip: 'sunt-hipoacuzic.mp4' }, { word: 'sunt surd/ă', clip: 'sunt-surd.mp4' }, { word: 'supermarket', clip: 'supermarket.mp4' }, { word: 'te pot ajuta', clip: 'te-pot-ajuta.mp4' }, { word: 'te rog', clip: 'te-rog.mp4' }, { word: 'telefon', clip: 'telefon.mp4' }, { word: 'teren', clip: 'teren.mp4' }, { word: 'toaletă', clip: 'toaleta.mp4' }, { word: 'tâmplărie', clip: 'tamplarie.mp4' }, { word: 'ulei', clip: 'ulei.mp4' }, { word: 'unde', clip: 'unde.mp4' }, { word: 'unit', clip: 'unit.mp4' }, { word: 'ureche', clip: 'ureche.mp4' }, { word: 'urgență', clip: 'urgenta.mp4' }, { word: 'ușă', clip: 'usa.mp4' }, { word: 'vecin', clip: 'vecin.mp4' }, { word: 'viitor', clip: 'viitor.mp4' }, { word: 'vopsea', clip: 'vopsea.mp4' }, { word: 'vreau', clip: 'vreau.mp4' }, { word: 'vrei', clip: 'vrei.mp4' }, { word: 'zidar', clip: 'zidar.mp4' }, { word: 'în', clip: 'in.mp4' }, { word: 'înainte', clip: 'inainte.mp4' }, { word: 'înapoi', clip: 'inapoi.mp4' }, { word: 'începem acum!', clip: 'incepem-acum.mp4' }, { word: 'încet', clip: 'incet.mp4' }, { word: 'încredere', clip: 'incredere.mp4' }, { word: 'șef', clip: 'sef.mp4' }, { word: 'șofer', clip: 'sofer.mp4' }, { word: 'șofer camion', clip: 'sofer-camion.mp4' }, { word: 'țară', clip: 'tara.mp4' }])
const wordsToGo = ref(words.value.slice())

// Create reactive references for the game state
const choices = ref([])
const correctAnswer = ref(null)
const selectedAnswer = ref(null)
const videoRef = ref(null)
const videoUrl = ref(null)
// percent between 0 and 100
const progress = ref(0)

const nextWords = () => {
  const shuffle = (arr) => {
    const a = arr.slice()
    for (let i = a.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1))
      ;[a[i], a[j]] = [a[j], a[i]]
    }
    return a
  }

  // If wordsToGo is empty (finished), pick from full list so UI stays stable.
  // Prefer picking from wordsToGo when available so the game progresses through remaining items.
  if (wordsToGo.value.length === 0) {
    correctAnswer.value = words.value[Math.floor(Math.random() * words.value.length)]
  } else {
    correctAnswer.value = wordsToGo.value[Math.floor(Math.random() * wordsToGo.value.length)]
  }

  // pool for the remaining choices: all words excluding the picked one (by reference)
  const pool = correctAnswer.value ? words.value.filter(w => w !== correctAnswer.value) : words.value.slice()
  const others = shuffle(pool).slice(0, 3)

  let result = []
  result.push(correctAnswer.value)
  result = result.concat(others)

  // return shuffled so the 'correctAnswer' isn't always first
  choices.value = shuffle(result)
  setVideoUrl('https://pesemne.ro/wp-content/uploads/clips/'+correctAnswer.value.clip)
}

// Function to check answer and generate new question
const checkAnswer = (selected) => {
  selectedAnswer.value = selected

  // increment progress if correct
  if (selected === correctAnswer.value) {
    // remove correct answer from wordsToGo
    wordsToGo.value = wordsToGo.value.filter(word => word !== correctAnswer.value)
    progress.value = Math.min(100, Math.floor(100 - ((wordsToGo.value.length / words.value.length) * 100)))

    localStorage.setItem(STORAGE_KEY, JSON.stringify(wordsToGo.value))
  }

  // Generate new choices after selection
  setTimeout(() => {
    selectedAnswer.value = null
    nextWords()
  }, 1500)
}

const setVideoUrl = (url) => {
  videoUrl.value = url
  if (videoRef.value) {
    videoRef.value.src = url
    videoRef.value.load()
  }
}

const loadDataFromStorage = () => {
  try {
    const raw = localStorage.getItem(STORAGE_KEY)
    if (raw) {
      const savedWords = JSON.parse(raw)
      if (Array.isArray(savedWords) && savedWords.length > 0) {
        wordsToGo.value = savedWords.slice()
      } else {
        wordsToGo.value = words.value.slice()
      }
    } else {
      wordsToGo.value = words.value.slice()
    }
  } catch (e) {
    console.error(e)
    wordsToGo.value = words.value.slice()
  }
}

onMounted(() => {
  loadDataFromStorage()

  // initialize progress based on what's left
  progress.value = Math.min(100, Math.floor(100 - ((wordsToGo.value.length / words.value.length) * 100)))

  nextWords()
  // try to play video (will work if video is muted/autoplay allowed)
  videoRef.value?.play().catch(() => {})
})
</script>

<template>
  <div class="quiz-container">
    <div class="progress-wrap" aria-hidden="false">
      <div class="progress-track">
        <div class="progress-bar" :style="{ width: progress + '%' }"></div>
      </div>
      <div class="progress-label">{{ progress }}%</div>
    </div>

    <h2>Alege varianta corectă</h2>

    <!-- Video adăugat deasupra variantelor -->
    <div class="video-wrap">
      <video
        ref="videoRef"
        :src="videoUrl"
        autoplay
        muted
        playsinline
        preload="metadata"
        controls
        loop>
        Your browser does not support the video tag.
      </video>
    </div>

    <div class="choices">
      <button
        v-for="(choice, index) in choices"
        :key="index"
        :class="{
          correct: selectedAnswer && choice === correctAnswer,
          wrong: selectedAnswer && choice === selectedAnswer && selectedAnswer !== correctAnswer
        }"
        @click="checkAnswer(choice)"
        :disabled="selectedAnswer !== null"
      >
        {{ choice.word }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.quiz-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.progress-wrap {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 12px;
}

.progress-track {
  flex: 1;
  height: 12px;
  background: #e9ecef;
  border-radius: 12px;
  overflow: hidden;
  box-shadow: inset 0 1px 2px rgba(0,0,0,0.05);
}

.progress-bar {
  height: 100%;
  background: linear-gradient(90deg, #4caf50, #2e7d32);
  width: 0%;
  transition: width 400ms ease;
}

.progress-label {
  min-width: 44px;
  text-align: right;
  font-size: 13px;
  color: #333;
}

.video-wrap {
  margin: 10px 0 20px;
}

.video-wrap video {
  width: 100%;
  height: auto;
  border-radius: 8px;
  background: #000;
}

.choices {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 10px;
  margin-top: 20px;
}

button {
  padding: 15px;
  font-size: 16px;
  cursor: pointer;
  border: 1px solid #ccc;
  border-radius: 4px;
  background: white;
  transition: background-color 150ms, border-color 150ms, color 150ms;
}

button:hover {
  background: #f0f0f0;
}

button.correct {
  background: #d4edda;
  border-color: #28a745;
  color: #155724;
}

button.wrong {
  background: #f8d7da;
  border-color: #dc3545;
  color: #721c24;
}

button:disabled {
  cursor: not-allowed;
}
</style>
