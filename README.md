@theme {
  --color-gray-50: oklch(0.985 0.002 247.858);
  --color-gray-100: oklch(0.97 0.005 247.858);
  --color-gray-200: oklch(0.922 0.013 247.858);
  --color-gray-300: oklch(0.875 0.02 247.858);
  --color-gray-400: oklch(0.748 0.026 247.858);
  --color-gray-500: oklch(0.646 0.032 247.858);
  --color-gray-600: oklch(0.545 0.038 247.858);
  --color-gray-700: oklch(0.445 0.044 247.858);
  --color-gray-800: oklch(0.345 0.051 247.858);
  --color-gray-900: oklch(0.156 0.064 247.858);
  --color-gray-950: oklch(0.078 0.083 247.858);
}

@import "tailwindcss";

/* Global styles */
* {
  box-sizing: border-box;
}

html,
body {
  max-width: 100vw;
  overflow-x: hidden;
}

body {
  color: rgb(var(--foreground-rgb));
  background: linear-gradient(
      to bottom,
      transparent,
      rgb(var(--background-end-rgb))
    )
    rgb(var(--background-start-rgb));
}

a {
  color: inherit;
  text-decoration: none;
}

@media (prefers-color-scheme: dark) {
  html {
    color-scheme: dark;
  }
}

/* Custom scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: rgba(255, 255, 255, 0.1);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb {
  background: rgba(139, 92, 246, 0.6);
  border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
  background: rgba(139, 92, 246, 0.8);
}

/* Animation utilities */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-in {
  animation: fadeIn 0.3s ease-out;
}

/* Glass effect utility */
.glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

/* Text truncation utility */
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

/* PWA specific styles */
@media (display-mode: standalone) {
  body {
    padding-top: env(safe-area-inset-top);
    padding-bottom: env(safe-area-inset-bottom);
  }
}

/* Mobile optimizations */
@media (max-width: 768px) {
  .container {
    padding-left: 1rem;
    padding-right: 1rem;
  }
}

/* Focus styles for accessibility */
button:focus-visible,
input:focus-visible,
select:focus-visible,
textarea:focus-visible {
  outline: 2px solid #8b5cf6;
  outline-offset: 2px;
}

/* Loading spinner */
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.animate-spin {
  animation: spin 1s linear infinite;
}

/* Gradient text utility */
.gradient-text {
  background: linear-gradient(135deg, #8b5cf6, #ec4899);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* Card hover effects */
.card-hover {
  transition: all 0.3s ease;
}

.card-hover:hover {
  transform: translateY(-2px);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

/* Button loading state */
.btn-loading {
  position: relative;
  color: transparent;
}

.btn-loading::after {
  content: "";
  position: absolute;
  width: 16px;
  height: 16px;
  top: 50%;
  left: 50%;
  margin-left: -8px;
  margin-top: -8px;
  border: 2px solid #ffffff;
  border-radius: 50%;
  border-top-color: transparent;
  animation: spin 1s linear infinite;
}

/* Responsive video container */
.video-container {
  position: relative;
  width: 100%;
  height: 0;
  padding-bottom: 56.25%; /* 16:9 aspect ratio */
}

.video-container iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

/* Custom radio and checkbox styles */
input[type="radio"]:checked,
input[type="checkbox"]:checked {
  background-color: #8b5cf6;
  border-color: #8b5cf6;
}

/* Toast notification styles */
.toast {
  background: rgba(0, 0, 0, 0.9);
  color: white;
  border: 1px solid rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
}

/* Progress bar styles */
.progress-bar {
  background: linear-gradient(90deg, #8b5cf6, #ec4899);
  transition: width 0.3s ease;
}

/* Image optimization */
img {
  max-width: 100%;
  height: auto;
}

/* Print styles */
@media print {
  .no-print {
    display: none !important;
  }
}

/* High contrast mode support */
@media (prefers-contrast: high) {
  .bg-black\/20 {
    background-color: rgba(0, 0, 0, 0.8);
  }
  
  .border-white\/10 {
    border-color: rgba(255, 255, 255, 0.5);
  }
}import type { Metadata } from "next";
import { Geist, Geist_Mono } from "next/font/google";
import "./globals.css";

const geistSans = Geist({
  variable: "--font-geist-sans",
  subsets: ["latin"],
});

const geistMono = Geist_Mono({
  variable: "--font-geist-mono",
  subsets: ["latin"],
});

export const metadata: Metadata = {
  title: "FitPro Academy - Treino e Nutrição",
  description: "Seu personal trainer e nutricionista no bolso. Treinos personalizados, análise de calorias por IA e consultoria nutricional.",
  manifest: "/manifest.json",
  themeColor: "#8b5cf6",
  viewport: "width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no",
  appleWebApp: {
    capable: true,
    statusBarStyle: "default",
    title: "FitPro Academy"
  }
};

export default function RootLayout({
  children,
}: Readonly<{
  children: React.ReactNode;
}>) {
  return (
    <html lang="pt-BR">
      <head>
        <link rel="manifest" href="/manifest.json" />
        <meta name="theme-color" content="#8b5cf6" />
        <meta name="apple-mobile-web-app-capable" content="yes" />
        <meta name="apple-mobile-web-app-status-bar-style" content="default" />
        <meta name="apple-mobile-web-app-title" content="FitPro Academy" />
        <link rel="apple-touch-icon" href="/icon-192.png" />
      </head>
      <body
        className={`${geistSans.variable} ${geistMono.variable} antialiased`}
      >
        {children}
      </body>
    </html>
  );
}"use client"

import { useState, useRef, useEffect } from 'react'
import { Button } from '@/components/ui/button'
import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs'
import { Badge } from '@/components/ui/badge'
import { Progress } from '@/components/ui/progress'
import { Dialog, DialogContent, DialogDescription, DialogHeader, DialogTitle, DialogTrigger } from '@/components/ui/dialog'
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select'
import { Textarea } from '@/components/ui/textarea'
import { 
  Dumbbell, 
  Camera, 
  MessageCircle, 
  Crown, 
  Play, 
  User, 
  Target, 
  Zap, 
  Star,
  Check,
  Upload,
  Bot,
  Stethoscope,
  CreditCard,
  Trophy,
  Calendar,
  TrendingUp
} from 'lucide-react'

interface UserProfile {
  height: string
  weight: string
  goal: string
  experience: string
}

interface Exercise {
  id: number
  name: string
  muscle: string
  sets: string
  reps: string
  videoUrl: string
  difficulty: 'Iniciante' | 'Intermediário' | 'Avançado'
  description: string
}

interface Plan {
  id: string
  name: string
  price: number
  features: string[]
  popular?: boolean
}

const exercises: Exercise[] = [
  // EXERCÍCIOS PARA INICIANTES (EXPANDIDO)
  {
    id: 1,
    name: "Caminhada na Esteira",
    muscle: "Cardio",
    sets: "1",
    reps: "20-30 min",
    videoUrl: "https://www.youtube.com/embed/9ZknEYboBOQ",
    difficulty: "Iniciante",
    description: "Exercício cardiovascular básico para iniciantes. Comece devagar e aumente gradualmente."
  },
  {
    id: 2,
    name: "Agachamento Livre (Peso Corporal)",
    muscle: "Pernas",
    sets: "3",
    reps: "10-15",
    videoUrl: "https://www.youtube.com/embed/YaXPRqUwItQ",
    difficulty: "Iniciante",
    description: "Movimento fundamental para fortalecer pernas e glúteos. Foque na postura correta."
  },
  {
    id: 3,
    name: "Flexão de Braço (Joelhos)",
    muscle: "Peito",
    sets: "3",
    reps: "8-12",
    videoUrl: "https://www.youtube.com/embed/jWxvty2KROs",
    difficulty: "Iniciante",
    description: "Versão modificada da flexão tradicional, ideal para iniciantes desenvolverem força."
  },
  {
    id: 4,
    name: "Prancha Isométrica",
    muscle: "Core",
    sets: "3",
    reps: "20-30 seg",
    videoUrl: "https://www.youtube.com/embed/ASdvN_XEl_c",
    difficulty: "Iniciante",
    description: "Exercício fundamental para fortalecer o core e melhorar a estabilidade."
  },
  {
    id: 5,
    name: "Puxada Frontal (Máquina)",
    muscle: "Costas",
    sets: "3",
    reps: "10-12",
    videoUrl: "https://www.youtube.com/embed/CAwf7n6Luuc",
    difficulty: "Iniciante",
    description: "Exercício básico para desenvolver a musculatura das costas de forma segura."
  },
  {
    id: 6,
    name: "Rosca Direta (Halteres Leves)",
    muscle: "Bíceps",
    sets: "3",
    reps: "12-15",
    videoUrl: "https://www.youtube.com/embed/ykJmrZ5v0Oo",
    difficulty: "Iniciante",
    description: "Exercício isolado para bíceps. Comece com pesos leves e foque na técnica."
  },
  {
    id: 7,
    name: "Elevação Lateral (Halteres)",
    muscle: "Ombros",
    sets: "3",
    reps: "10-12",
    videoUrl: "https://www.youtube.com/embed/3VcKaXpzqRo",
    difficulty: "Iniciante",
    description: "Exercício para desenvolver os ombros laterais. Use pesos leves no início."
  },
  {
    id: 8,
    name: "Tríceps na Polia (Corda)",
    muscle: "Tríceps",
    sets: "3",
    reps: "12-15",
    videoUrl: "https://www.youtube.com/embed/2-LAMcpzODU",
    difficulty: "Iniciante",
    description: "Exercício seguro para iniciantes trabalharem o tríceps com controle total."
  },
  {
    id: 9,
    name: "Leg Press 45°",
    muscle: "Pernas",
    sets: "3",
    reps: "12-15",
    videoUrl: "https://www.youtube.com/embed/IZxyjW7MPJQ",
    difficulty: "Iniciante",
    description: "Alternativa segura ao agachamento livre para iniciantes fortalecerem as pernas."
  },
  {
    id: 10,
    name: "Remada Sentada (Máquina)",
    muscle: "Costas",
    sets: "3",
    reps: "10-12",
    videoUrl: "https://www.youtube.com/embed/xQNrFHEMhI4",
    difficulty: "Iniciante",
    description: "Exercício fundamental para desenvolver a musculatura das costas de forma controlada."
  },
  {
    id: 11,
    name: "Panturrilha em Pé",
    muscle: "Panturrilha",
    sets: "3",
    reps: "15-20",
    videoUrl: "https://www.youtube.com/embed/gwLzBJYoWlI",
    difficulty: "Iniciante",
    description: "Exercício simples para fortalecer as panturrilhas e melhorar a estabilidade."
  },
  {
    id: 12,
    name: "Abdominal Tradicional",
    muscle: "Core",
    sets: "3",
    reps: "15-20",
    videoUrl: "https://www.youtube.com/embed/1fbU_MkV7NE",
    difficulty: "Iniciante",
    description: "Exercício clássico para fortalecer a musculatura abdominal superior."
  },
  {
    id: 13,
    name: "Alongamento Geral",
    muscle: "Flexibilidade",
    sets: "1",
    reps: "10-15 min",
    videoUrl: "https://www.youtube.com/embed/g_tea8ZNk5A",
    difficulty: "Iniciante",
    description: "Rotina de alongamento essencial para recuperação e flexibilidade."
  },
  {
    id: 14,
    name: "Cadeira Extensora",
    muscle: "Quadríceps",
    sets: "3",
    reps: "12-15",
    videoUrl: "https://www.youtube.com/embed/YyvSfVjQeL0",
    difficulty: "Iniciante",
    description: "Exercício isolado para quadríceps, ideal para iniciantes aprenderem o movimento."
  },
  {
    id: 15,
    name: "Mesa Flexora",
    muscle: "Posterior",
    sets: "3",
    reps: "12-15",
    videoUrl: "https://www.youtube.com/embed/1Tq3QdYUuHs",
    difficulty: "Iniciante",
    description: "Exercício para fortalecer a parte posterior das coxas de forma segura."
  },

  // EXERCÍCIOS INTERMEDIÁRIOS E AVANÇADOS
  {
    id: 16,
    name: "Supino Reto",
    muscle: "Peito",
    sets: "3-4",
    reps: "8-12",
    videoUrl: "https://www.youtube.com/embed/rT7DgCr-3pg",
    difficulty: "Intermediário",
    description: "Exercício fundamental para desenvolvimento do peitoral maior."
  },
  {
    id: 17,
    name: "Agachamento Livre (Com Peso)",
    muscle: "Pernas",
    sets: "4",
    reps: "10-15",
    videoUrl: "https://www.youtube.com/embed/ultWZbUMPL8",
    difficulty: "Intermediário",
    description: "Exercício composto essencial para desenvolvimento das pernas e glúteos."
  },
  {
    id: 18,
    name: "Desenvolvimento com Halteres",
    muscle: "Ombros",
    sets: "3",
    reps: "10-12",
    videoUrl: "https://www.youtube.com/embed/qEwKCR5JCog",
    difficulty: "Intermediário",
    description: "Exercício para desenvolvimento completo dos ombros."
  },
  {
    id: 19,
    name: "Tríceps Testa",
    muscle: "Tríceps",
    sets: "3",
    reps: "10-12",
    videoUrl: "https://www.youtube.com/embed/d_KZxkY_0cM",
    difficulty: "Intermediário",
    description: "Exercício isolado eficaz para desenvolvimento do tríceps."
  },
  {
    id: 20,
    name: "Levantamento Terra",
    muscle: "Costas/Pernas",
    sets: "4",
    reps: "6-8",
    videoUrl: "https://www.youtube.com/embed/ytGaGIn3SjE",
    difficulty: "Avançado",
    description: "Exercício composto avançado que trabalha múltiplos grupos musculares."
  }
]

const plans: Plan[] = [
  {
    id: 'basic',
    name: 'Plano Básico',
    price: 59,
    features: [
      'Treinos personalizados',
      'Análise básica de calorias',
      'Suporte por email',
      'Acesso a exercícios básicos',
      '15 exercícios para iniciantes'
    ]
  },
  {
    id: 'premium',
    name: 'Plano Premium',
    price: 149,
    popular: true,
    features: [
      'Tudo do Plano Básico',
      'Chat com IA 24/7',
      'Análise avançada de fotos',
      'Planos de dieta personalizados',
      'Vídeos HD de exercícios',
      'Acompanhamento de progresso',
      'Acesso a todos os exercícios'
    ]
  },
  {
    id: 'elite',
    name: 'Plano Elite',
    price: 249,
    features: [
      'Tudo do Plano Premium',
      'Consultas com nutricionista',
      'Personal trainer virtual',
      'Planos de suplementação',
      'Acesso prioritário a novidades',
      'Relatórios detalhados de progresso',
      'Treinos personalizados semanais'
    ]
  }
]

export default function FitApp() {
  const [showInstallPrompt, setShowInstallPrompt] = useState(false)
  const [activeTab, setActiveTab] = useState('profile')
  const [userProfile, setUserProfile] = useState<UserProfile>({
    height: '',
    weight: '',
    goal: '',
    experience: ''
  })
  const [selectedExercise, setSelectedExercise] = useState<Exercise | null>(null)
  const [uploadedImage, setUploadedImage] = useState<string | null>(null)
  const [calorieAnalysis, setCalorieAnalysis] = useState<any>(null)
  const [chatMessages, setChatMessages] = useState<Array<{type: 'user' | 'ai' | 'nutritionist', message: string}>>([])
  const [currentMessage, setCurrentMessage] = useState('')
  const [selectedPlan, setSelectedPlan] = useState<string | null>(null)
  const [isProcessingPayment, setIsProcessingPayment] = useState(false)
  const fileInputRef = useRef<HTMLInputElement>(null)

  // Detectar se pode instalar PWA
  useEffect(() => {
    if (typeof window !== 'undefined') {
      window.addEventListener('beforeinstallprompt', (e) => {
        e.preventDefault()
        setShowInstallPrompt(true)
      })
    }
  }, [])

  const installPWA = () => {
    if (typeof window !== 'undefined' && 'serviceWorker' in navigator) {
      // Trigger install prompt
      setShowInstallPrompt(false)
      alert('Para instalar: No Chrome/Safari, toque no menu (⋮) e selecione "Instalar app" ou "Adicionar à tela inicial"')
    }
  }

  const handleProfileSubmit = () => {
    if (userProfile.height && userProfile.weight && userProfile.goal && userProfile.experience) {
      setActiveTab('workout')
    }
  }

  const getRecommendedExercises = () => {
    if (!userProfile.experience) return exercises.filter(ex => ex.difficulty === 'Iniciante').slice(0, 8)

    if (userProfile.experience === 'iniciante') {
      return exercises.filter(ex => ex.difficulty === 'Iniciante')
    } else if (userProfile.experience === 'intermediario') {
      return exercises.filter(ex => ex.difficulty === 'Iniciante' || ex.difficulty === 'Intermediário')
    }
    return exercises
  }

  const handleImageUpload = (event: React.ChangeEvent<HTMLInputElement>) => {
    const file = event.target.files?.[0]
    if (file) {
      const reader = new FileReader()
      reader.onload = (e) => {
        setUploadedImage(e.target?.result as string)
        // Simular análise de calorias
        setTimeout(() => {
          setCalorieAnalysis({
            totalCalories: Math.floor(Math.random() * 800) + 200,
            protein: Math.floor(Math.random() * 50) + 10,
            carbs: Math.floor(Math.random() * 80) + 20,
            fat: Math.floor(Math.random() * 30) + 5,
            foods: [
              'Arroz branco - 150 calorias',
              'Frango grelhado - 200 calorias',
              'Brócolis - 25 calorias',
              'Azeite - 80 calorias'
            ]
          })
        }, 2000)
      }
      reader.readAsDataURL(file)
    }
  }

  const sendMessage = (type: 'ai' | 'nutritionist') => {
    if (!currentMessage.trim()) return

    setChatMessages(prev => [...prev, { type: 'user', message: currentMessage }])
    
    setTimeout(() => {
      const response = type === 'ai' 
        ? `IA: Baseado na sua pergunta "${currentMessage}", recomendo focar em exercícios compostos e manter uma dieta balanceada. Posso ajudar com um plano específico!`
        : `Nutricionista: Olá! Sobre "${currentMessage}", é importante considerar seus objetivos individuais. Vamos agendar uma consulta para um plano personalizado?`
      
      setChatMessages(prev => [...prev, { type, message: response }])
    }, 1000)

    setCurrentMessage('')
  }

  const handlePlanSelection = async (planId: string) => {
    const plan = plans.find(p => p.id === planId)
    if (!plan) return

    setIsProcessingPayment(true)
    setSelectedPlan(planId)

    try {
      // Simular processamento de pagamento
      await new Promise(resolve => setTimeout(resolve, 2000))
      
      alert(`Plano ${plan.name} selecionado! Redirecionando para pagamento...`)
      
    } catch (error) {
      console.error('Erro ao processar pagamento:', error)
      alert('Erro ao processar pagamento. Tente novamente.')
    } finally {
      setIsProcessingPayment(false)
    }
  }

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900">
      {/* Header */}
      <header className="bg-black/20 backdrop-blur-sm border-b border-white/10">
        <div className="container mx-auto px-4 py-4">
          <div className="flex items-center justify-between">
            <div className="flex items-center gap-2">
              <Dumbbell className="h-8 w-8 text-purple-400" />
              <h1 className="text-2xl font-bold text-white">FitPro Academy</h1>
            </div>
            <div className="flex items-center gap-2">
              {showInstallPrompt && (
                <Button 
                  onClick={installPWA}
                  size="sm" 
                  className="bg-green-600 hover:bg-green-700 text-white"
                >
                  📱 Instalar App
                </Button>
              )}
              <Badge variant="secondary" className="bg-purple-600 text-white">
                <Crown className="h-4 w-4 mr-1" />
                Premium
              </Badge>
            </div>
          </div>
        </div>
      </header>

      <div className="container mx-auto px-4 py-8">
        <Tabs value={activeTab} onValueChange={setActiveTab} className="w-full">
          <TabsList className="grid w-full grid-cols-5 bg-black/20 backdrop-blur-sm">
            <TabsTrigger value="profile" className="data-[state=active]:bg-purple-600">
              <User className="h-4 w-4 mr-2" />
              Perfil
            </TabsTrigger>
            <TabsTrigger value="workout" className="data-[state=active]:bg-purple-600">
              <Dumbbell className="h-4 w-4 mr-2" />
              Treino
            </TabsTrigger>
            <TabsTrigger value="nutrition" className="data-[state=active]:bg-purple-600">
              <Camera className="h-4 w-4 mr-2" />
              Nutrição
            </TabsTrigger>
            <TabsTrigger value="support" className="data-[state=active]:bg-purple-600">
              <MessageCircle className="h-4 w-4 mr-2" />
              Suporte
            </TabsTrigger>
            <TabsTrigger value="plans" className="data-[state=active]:bg-purple-600">
              <Crown className="h-4 w-4 mr-2" />
              Planos
            </TabsTrigger>
          </TabsList>

          {/* Perfil do Usuário */}
          <TabsContent value="profile" className="space-y-6">
            <Card className="bg-black/20 backdrop-blur-sm border-white/10">
              <CardHeader>
                <CardTitle className="text-white flex items-center gap-2">
                  <Target className="h-5 w-5 text-purple-400" />
                  Configure seu Perfil
                </CardTitle>
                <CardDescription className="text-gray-300">
                  Vamos personalizar seu treino baseado no seu perfil
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-4">
                <div className="grid grid-cols-1 md:grid-cols-2 gap-4">
                  <div>
                    <Label htmlFor="height" className="text-white">Altura (cm)</Label>
                    <Input
                      id="height"
                      type="number"
                      placeholder="175"
                      value={userProfile.height}
                      onChange={(e) => setUserProfile(prev => ({ ...prev, height: e.target.value }))}
                      className="bg-white/10 border-white/20 text-white placeholder:text-gray-400"
                    />
                  </div>
                  <div>
                    <Label htmlFor="weight" className="text-white">Peso (kg)</Label>
                    <Input
                      id="weight"
                      type="number"
                      placeholder="70"
                      value={userProfile.weight}
                      onChange={(e) => setUserProfile(prev => ({ ...prev, weight: e.target.value }))}
                      className="bg-white/10 border-white/20 text-white placeholder:text-gray-400"
                    />
                  </div>
                </div>
                
                <div>
                  <Label className="text-white">Objetivo Principal</Label>
                  <Select value={userProfile.goal} onValueChange={(value) => setUserProfile(prev => ({ ...prev, goal: value }))}>
                    <SelectTrigger className="bg-white/10 border-white/20 text-white">
                      <SelectValue placeholder="Selecione seu objetivo" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="perder-peso">Perder Peso</SelectItem>
                      <SelectItem value="ganhar-massa">Ganhar Massa Muscular</SelectItem>
                      <SelectItem value="definir">Definir Músculos</SelectItem>
                      <SelectItem value="resistencia">Melhorar Resistência</SelectItem>
                    </SelectContent>
                  </Select>
                </div>

                <div>
                  <Label className="text-white">Nível de Experiência</Label>
                  <Select value={userProfile.experience} onValueChange={(value) => setUserProfile(prev => ({ ...prev, experience: value }))}>
                    <SelectTrigger className="bg-white/10 border-white/20 text-white">
                      <SelectValue placeholder="Selecione sua experiência" />
                    </SelectTrigger>
                    <SelectContent>
                      <SelectItem value="iniciante">Iniciante (0-6 meses)</SelectItem>
                      <SelectItem value="intermediario">Intermediário (6 meses - 2 anos)</SelectItem>
                      <SelectItem value="avancado">Avançado (2+ anos)</SelectItem>
                    </SelectContent>
                  </Select>
                </div>

                <Button 
                  onClick={handleProfileSubmit}
                  className="w-full bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700"
                  disabled={!userProfile.height || !userProfile.weight || !userProfile.goal || !userProfile.experience}
                >
                  <Zap className="h-4 w-4 mr-2" />
                  Gerar Treino Personalizado
                </Button>
              </CardContent>
            </Card>
          </TabsContent>

          {/* Treinos */}
          <TabsContent value="workout" className="space-y-6">
            <Card className="bg-black/20 backdrop-blur-sm border-white/10">
              <CardHeader>
                <CardTitle className="text-white flex items-center gap-2">
                  <Trophy className="h-5 w-5 text-purple-400" />
                  Seus Exercícios Recomendados
                </CardTitle>
                <CardDescription className="text-gray-300">
                  Baseado no seu perfil: {userProfile.goal} - Nível {userProfile.experience}
                  <br />
                  <span className="text-purple-400 font-semibold">
                    {getRecommendedExercises().length} exercícios disponíveis para seu nível
                  </span>
                </CardDescription>
              </CardHeader>
              <CardContent>
                <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                  {getRecommendedExercises().map((exercise) => (
                    <Card key={exercise.id} className="bg-white/5 border-white/10 hover:bg-white/10 transition-colors">
                      <CardContent className="p-4">
                        <div className="flex justify-between items-start mb-2">
                          <h3 className="font-semibold text-white text-sm">{exercise.name}</h3>
                          <Badge variant="outline" className="text-xs">
                            {exercise.difficulty}
                          </Badge>
                        </div>
                        <p className="text-sm text-gray-300 mb-1">Músculo: {exercise.muscle}</p>
                        <p className="text-sm text-gray-400 mb-2">
                          {exercise.sets} séries × {exercise.reps} repetições
                        </p>
                        <p className="text-xs text-gray-500 mb-3 line-clamp-2">
                          {exercise.description}
                        </p>
                        <Dialog>
                          <DialogTrigger asChild>
                            <Button 
                              size="sm" 
                              className="w-full bg-purple-600 hover:bg-purple-700"
                              onClick={() => setSelectedExercise(exercise)}
                            >
                              <Play className="h-4 w-4 mr-2" />
                              Ver Vídeo
                            </Button>
                          </DialogTrigger>
                          <DialogContent className="max-w-3xl bg-black/90 border-white/20">
                            <DialogHeader>
                              <DialogTitle className="text-white">{selectedExercise?.name}</DialogTitle>
                              <DialogDescription className="text-gray-300">
                                {selectedExercise?.description}
                              </DialogDescription>
                            </DialogHeader>
                            <div className="aspect-video">
                              <iframe
                                src={selectedExercise?.videoUrl}
                                className="w-full h-full rounded-lg"
                                allowFullScreen
                              />
                            </div>
                            <div className="text-white space-y-2">
                              <p><strong>Músculo trabalhado:</strong> {selectedExercise?.muscle}</p>
                              <p><strong>Séries:</strong> {selectedExercise?.sets}</p>
                              <p><strong>Repetições:</strong> {selectedExercise?.reps}</p>
                              <p><strong>Dificuldade:</strong> {selectedExercise?.difficulty}</p>
                            </div>
                          </DialogContent>
                        </Dialog>
                      </CardContent>
                    </Card>
                  ))}
                </div>
              </CardContent>
            </Card>
          </TabsContent>

          {/* Nutrição */}
          <TabsContent value="nutrition" className="space-y-6">
            <Card className="bg-black/20 backdrop-blur-sm border-white/10">
              <CardHeader>
                <CardTitle className="text-white flex items-center gap-2">
                  <Camera className="h-5 w-5 text-purple-400" />
                  Análise de Calorias por Foto
                </CardTitle>
                <CardDescription className="text-gray-300">
                  Tire uma foto do seu prato e descubra as calorias
                </CardDescription>
              </CardHeader>
              <CardContent className="space-y-4">
                <div className="border-2 border-dashed border-white/20 rounded-lg p-8 text-center">
                  {uploadedImage ? (
                    <div className="space-y-4">
                      <img 
                        src={uploadedImage} 
                        alt="Prato analisado" 
                        className="max-w-full h-64 object-cover rounded-lg mx-auto"
                      />
                      {calorieAnalysis ? (
                        <div className="bg-white/10 rounded-lg p-4 text-left">
                          <h3 className="text-white font-semibold mb-3">Análise Nutricional:</h3>
                          <div className="grid grid-cols-2 md:grid-cols-4 gap-4 mb-4">
                            <div className="text-center">
                              <div className="text-2xl font-bold text-purple-400">{calorieAnalysis.totalCalories}</div>
                              <div className="text-sm text-gray-300">Calorias</div>
                            </div>
                            <div className="text-center">
                              <div className="text-2xl font-bold text-blue-400">{calorieAnalysis.protein}g</div>
                              <div className="text-sm text-gray-300">Proteína</div>
                            </div>
                            <div className="text-center">
                              <div className="text-2xl font-bold text-green-400">{calorieAnalysis.carbs}g</div>
                              <div className="text-sm text-gray-300">Carboidratos</div>
                            </div>
                            <div className="text-center">
                              <div className="text-2xl font-bold text-yellow-400">{calorieAnalysis.fat}g</div>
                              <div className="text-sm text-gray-300">Gorduras</div>
                            </div>
                          </div>
                          <div className="text-white">
                            <h4 className="font-semibold mb-2">Alimentos identificados:</h4>
                            <ul className="space-y-1">
                              {calorieAnalysis.foods.map((food: string, index: number) => (
                                <li key={index} className="text-sm text-gray-300">• {food}</li>
                              ))}
                            </ul>
                          </div>
                        </div>
                      ) : (
                        <div className="text-white">
                          <div className="animate-spin rounded-full h-8 w-8 border-b-2 border-purple-400 mx-auto mb-2"></div>
                          <p>Analisando sua refeição...</p>
                        </div>
                      )}
                    </div>
                  ) : (
                    <div className="text-white">
                      <Upload className="h-12 w-12 mx-auto mb-4 text-purple-400" />
                      <p className="mb-4">Clique para enviar uma foto do seu prato</p>
                      <Button 
                        onClick={() => fileInputRef.current?.click()}
                        className="bg-purple-600 hover:bg-purple-700"
                      >
                        <Camera className="h-4 w-4 mr-2" />
                        Enviar Foto
                      </Button>
                      <input
                        ref={fileInputRef}
                        type="file"
                        accept="image/*"
                        onChange={handleImageUpload}
                        className="hidden"
                      />
                    </div>
                  )}
                </div>
                
                {uploadedImage && (
                  <Button 
                    onClick={() => {
                      setUploadedImage(null)
                      setCalorieAnalysis(null)
                    }}
                    variant="outline"
                    className="w-full border-white/20 text-white hover:bg-white/10"
                  >
                    Analisar Nova Foto
                  </Button>
                )}
              </CardContent>
            </Card>
          </TabsContent>

          {/* Suporte */}
          <TabsContent value="support" className="space-y-6">
            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              {/* Chat com IA */}
              <Card className="bg-black/20 backdrop-blur-sm border-white/10">
                <CardHeader>
                  <CardTitle className="text-white flex items-center gap-2">
                    <Bot className="h-5 w-5 text-purple-400" />
                    Chat com IA
                  </CardTitle>
                  <CardDescription className="text-gray-300">
                    Tire suas dúvidas sobre treino e nutrição
                  </CardDescription>
                </CardHeader>
                <CardContent className="space-y-4">
                  <div className="h-64 bg-white/5 rounded-lg p-4 overflow-y-auto space-y-2">
                    {chatMessages.filter(msg => msg.type === 'user' || msg.type === 'ai').map((msg, index) => (
                      <div key={index} className={`p-2 rounded-lg ${
                        msg.type === 'user' 
                          ? 'bg-purple-600 text-white ml-8' 
                          : 'bg-white/10 text-gray-200 mr-8'
                      }`}>
                        {msg.message}
                      </div>
                    ))}
                  </div>
                  <div className="flex gap-2">
                    <Input
                      placeholder="Digite sua pergunta..."
                      value={currentMessage}
                      onChange={(e) => setCurrentMessage(e.target.value)}
                      className="bg-white/10 border-white/20 text-white placeholder:text-gray-400"
                      onKeyPress={(e) => e.key === 'Enter' && sendMessage('ai')}
                    />
                    <Button 
                      onClick={() => sendMessage('ai')}
                      className="bg-purple-600 hover:bg-purple-700"
                    >
                      Enviar
                    </Button>
                  </div>
                </CardContent>
              </Card>

              {/* Chat com Nutricionista */}
              <Card className="bg-black/20 backdrop-blur-sm border-white/10">
                <CardHeader>
                  <CardTitle className="text-white flex items-center gap-2">
                    <Stethoscope className="h-5 w-5 text-green-400" />
                    Nutricionista Online
                  </CardTitle>
                  <CardDescription className="text-gray-300">
                    Fale diretamente com um profissional
                  </CardDescription>
                </CardHeader>
                <CardContent className="space-y-4">
                  <div className="h-64 bg-white/5 rounded-lg p-4 overflow-y-auto space-y-2">
                    {chatMessages.filter(msg => msg.type === 'user' || msg.type === 'nutritionist').map((msg, index) => (
                      <div key={index} className={`p-2 rounded-lg ${
                        msg.type === 'user' 
                          ? 'bg-green-600 text-white ml-8' 
                          : 'bg-white/10 text-gray-200 mr-8'
                      }`}>
                        {msg.message}
                      </div>
                    ))}
                  </div>
                  <div className="flex gap-2">
                    <Input
                      placeholder="Fale com o nutricionista..."
                      value={currentMessage}
                      onChange={(e) => setCurrentMessage(e.target.value)}
                      className="bg-white/10 border-white/20 text-white placeholder:text-gray-400"
                      onKeyPress={(e) => e.key === 'Enter' && sendMessage('nutritionist')}
                    />
                    <Button 
                      onClick={() => sendMessage('nutritionist')}
                      className="bg-green-600 hover:bg-green-700"
                    >
                      Enviar
                    </Button>
                  </div>
                </CardContent>
              </Card>
            </div>
          </TabsContent>

          {/* Planos */}
          <TabsContent value="plans" className="space-y-6">
            <div className="text-center mb-8">
              <h2 className="text-3xl font-bold text-white mb-4">Escolha seu Plano</h2>
              <p className="text-gray-300">Desbloqueie todo o potencial do FitPro Academy</p>
            </div>

            <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
              {plans.map((plan) => (
                <Card key={plan.id} className={`relative bg-black/20 backdrop-blur-sm border-white/10 ${
                  plan.popular ? 'ring-2 ring-purple-500' : ''
                }`}>
                  {plan.popular && (
                    <div className="absolute -top-3 left-1/2 transform -translate-x-1/2">
                      <Badge className="bg-purple-600 text-white">
                        <Star className="h-3 w-3 mr-1" />
                        Mais Popular
                      </Badge>
                    </div>
                  )}
                  <CardHeader className="text-center">
                    <CardTitle className="text-white text-xl">{plan.name}</CardTitle>
                    <div className="text-3xl font-bold text-purple-400">
                      R$ {plan.price}
                      <span className="text-sm text-gray-400">/mês</span>
                    </div>
                  </CardHeader>
                  <CardContent className="space-y-4">
                    <ul className="space-y-2">
                      {plan.features.map((feature, index) => (
                        <li key={index} className="flex items-center text-gray-300">
                          <Check className="h-4 w-4 text-green-400 mr-2 flex-shrink-0" />
                          {feature}
                        </li>
                      ))}
                    </ul>
                    <Button 
                      onClick={() => handlePlanSelection(plan.id)}
                      disabled={isProcessingPayment}
                      className={`w-full ${
                        plan.popular 
                          ? 'bg-gradient-to-r from-purple-600 to-pink-600 hover:from-purple-700 hover:to-pink-700' 
                          : 'bg-white/10 hover:bg-white/20 text-white'
                      }`}
                    >
                      <CreditCard className="h-4 w-4 mr-2" />
                      {isProcessingPayment && selectedPlan === plan.id 
                        ? 'Processando...' 
                        : 'Assinar Agora'
                      }
                    </Button>
                  </CardContent>
                </Card>
              ))}
            </div>

            {/* Informações sobre pagamento */}
            <Card className="bg-black/20 backdrop-blur-sm border-white/10">
              <CardContent className="p-6">
                <div className="text-center text-gray-300">
                  <h3 className="text-white font-semibold mb-2">💳 Pagamento Seguro</h3>
                  <p className="text-sm mb-4">
                    Aceitamos cartão de crédito, débito, PIX e boleto bancário.
                    <br />
                    Seus dados estão protegidos com criptografia de ponta.
                  </p>
                  <div className="flex justify-center items-center gap-4 text-xs">
                    <span>✅ Cancelamento a qualquer momento</span>
                    <span>✅ Suporte 24/7</span>
                    <span>✅ Garantia de 7 dias</span>
                  </div>
                </div>
              </CardContent>
            </Card>
          </TabsContent>
        </Tabs>
      </div>
    </div>
  )
}