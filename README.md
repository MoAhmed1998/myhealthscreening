<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Adult Preventive Screening Checklist</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" rel="stylesheet">
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #f0f7ff;
        }
        .language-selector {
            position: relative;
            background-color: #f8fafc;
            padding: 10px 0;
            text-align: center;
            z-index: 10;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            border-bottom: 1px solid #e2e8f0;
        }
        .language-flag {
            display: inline-flex;
            align-items: center;
            margin: 0 15px;
            padding: 6px 12px;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s;
            font-size: 16px;
            font-weight: 500;
        }
        .language-flag.active {
            background-color: rgba(59, 130, 246, 0.1);
            font-weight: 600;
        }
        .language-flag:hover {
            background-color: rgba(59, 130, 246, 0.05);
        }
        .language-flag span.flag {
            margin-right: 8px;
            font-size: 20px;
        }
        .print-only {
            display: none;
        }
        .why-it-matters {
            font-weight: 600;
            color: #2563eb;
        }
        .talk-with-doctor {
            background-color: #fffbeb;
            border-left: 3px solid #f59e0b;
            padding: 6px 10px;
            margin-top: 8px;
            border-radius: 0 6px 6px 0;
        }
        .grade-badge {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            font-weight: bold;
            font-size: 18px;
            margin-right: 12px;
            color: white;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .grade-a {
            background: linear-gradient(135deg, #4ade80, #22c55e);
        }
        .grade-b {
            background: linear-gradient(135deg, #60a5fa, #3b82f6);
        }
        .screening-grade-badge {
            position: absolute;
            top: 10px;
            right: 10px;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        .grade-item {
            display: flex;
            align-items: center;
            padding: 12px;
            border-radius: 12px;
            transition: all 0.2s;
            background-color: rgba(255,255,255,0.5);
            margin-bottom: 10px;
        }
        .grade-item:hover {
            background-color: rgba(255,255,255,0.9);
            transform: translateY(-2px);
        }
        .grade-icon {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 48px;
            height: 48px;
            border-radius: 12px;
            margin-right: 16px;
            color: white;
            font-size: 24px;
            box-shadow: 0 4px 6px rgba(59, 130, 246, 0.2);
        }
        .grade-icon-a {
            background: linear-gradient(135deg, #4ade80, #22c55e);
        }
        .grade-icon-b {
            background: linear-gradient(135deg, #60a5fa, #3b82f6);
        }
        .disclaimer {
            background-color: #f8fafc;
            border: 1px solid #e2e8f0;
            border-radius: 8px;
            padding: 16px;
            margin-top: 24px;
            text-align: center;
            font-style: italic;
            color: #64748b;
        }
        .radio-option {
            display: inline-flex;
            align-items: center;
            margin-right: 20px;
            cursor: pointer;
        }
        .radio-option input {
            margin-right: 6px;
        }
        .height-inputs {
            display: flex;
            align-items: center;
        }
        .height-inputs input {
            width: 70px;
            margin-right: 8px;
        }
        .height-inputs span {
            margin-right: 12px;
        }
        @media print {
            .no-print {
                display: none !important;
            }
            .print-only {
                display: block !important;
            }
            body {
                background-color: white;
                padding: 20px;
            }
            .results-container {
                box-shadow: none !important;
                border: 1px solid #ddd;
            }
        }
    </style>
</head>
<body class="min-h-screen">
    <!-- Language Selector -->
    <div class="language-selector no-print">
        <div class="language-flag active" data-lang="en">
            <span class="flag">🇺🇸</span>
            <span>English</span>
        </div>
        <div class="language-flag" data-lang="es">
            <span class="flag">🇪🇸</span>
            <span>Español</span>
        </div>
        <div class="language-flag" data-lang="pt">
            <span class="flag">🇵🇹</span>
            <span>Português</span>
        </div>
    </div>

    <div class="container mx-auto px-4 mt-8 max-w-4xl">
        <!-- Print-only header -->
        <div class="print-only mb-8">
            <h2 class="text-2xl font-bold mb-2">Preventive Screening Results</h2>
            <div class="grid grid-cols-2 gap-4">
                <div>
                    <p><strong>Age:</strong> <span id="printAge"></span></p>
                    <p><strong>Sex assigned at birth:</strong> <span id="printSex"></span></p>
                    <p><strong>BMI:</strong> <span id="printBMI"></span></p>
                </div>
                <div>
                    <p><strong>Date:</strong> <span id="printDate"></span></p>
                </div>
            </div>
            <hr class="my-4">
        </div>

        <!-- Title -->
        <div class="text-center mb-8">
            <h1 class="text-4xl font-bold text-blue-800" id="mainTitle">Adult Preventive Screening Checklist</h1>
            <p class="text-lg text-blue-600 mt-2" id="mainSubtitle">Find out which health screenings are recommended for you</p>
        </div>

        <!-- Input Form -->
        <div class="bg-white rounded-xl shadow-lg p-6 mb-8">
            <div class="grid md:grid-cols-2 gap-6">
                <div>
                    <label for="age" class="block text-gray-700 font-medium mb-2" id="ageLabel">
                        <i class="fas fa-birthday-cake text-blue-500 mr-2"></i>Enter your age:
                    </label>
                    <input type="number" id="age" min="18" max="120" class="w-full px-4 py-2 border border-blue-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Age (18-120)">
                </div>
                <div>
                    <label for="gender" class="block text-gray-700 font-medium mb-2" id="sexLabel">
                        <i class="fas fa-venus-mars text-blue-500 mr-2"></i>Select your sex assigned at birth:
                    </label>
                    <select id="gender" class="w-full px-4 py-2 border border-blue-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500">
                        <option value="" id="selectOption">Please select</option>
                        <option value="male" id="maleOption">Male (assigned at birth)</option>
                        <option value="female" id="femaleOption">Female (assigned at birth)</option>
                    </select>
                </div>
            </div>

            <!-- Height and Weight Section -->
            <div class="grid md:grid-cols-2 gap-6 mt-6">
                <div>
                    <label class="block text-gray-700 font-medium mb-2" id="heightLabel">
                        <i class="fas fa-ruler-vertical text-blue-500 mr-2"></i>Height:
                    </label>
                    <div class="height-inputs">
                        <input type="number" id="heightFeet" min="3" max="8" class="px-4 py-2 border border-blue-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Feet">
                        <span id="feetText">ft</span>
                        <input type="number" id="heightInches" min="0" max="11" class="px-4 py-2 border border-blue-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Inches">
                        <span id="inchesText">in</span>
                    </div>
                </div>
                <div>
                    <label for="weight" class="block text-gray-700 font-medium mb-2" id="weightLabel">
                        <i class="fas fa-weight text-blue-500 mr-2"></i>Weight:
                    </label>
                    <div class="flex items-center">
                        <input type="number" id="weight" min="50" max="500" class="w-full px-4 py-2 border border-blue-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" placeholder="Weight">
                        <span class="ml-2" id="poundsText">lbs</span>
                    </div>
                </div>
            </div>

            <!-- Additional Questions Section -->
            <div class="mt-6">
                <h3 class="text-lg font-semibold text-blue-800 mb-3" id="additionalQuestionsTitle">Additional Health Information</h3>
                
                <!-- Pregnant Question (only shown for females) -->
                <div id="pregnantQuestion" class="mb-4 hidden">
                    <label class="block text-gray-700 font-medium mb-2" id="pregnantLabel">
                        <i class="fas fa-baby text-blue-500 mr-2"></i>Are you currently pregnant?
                    </label>
                    <div>
                        <label class="radio-option">
                            <input type="radio" name="pregnant" value="yes">
                            <span id="pregnantYes">Yes</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="pregnant" value="no" checked>
                            <span id="pregnantNo">No</span>
                        </label>
                    </div>
                </div>
                
                <!-- Tobacco Use Question -->
                <div class="mb-4">
                    <label class="block text-gray-700 font-medium mb-2" id="tobaccoLabel">
                        <i class="fas fa-smoking text-blue-500 mr-2"></i>Have you ever used tobacco products?
                    </label>
                    <div>
                        <label class="radio-option">
                            <input type="radio" name="tobacco" value="yes">
                            <span id="tobaccoYes">Yes</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="tobacco" value="no" checked>
                            <span id="tobaccoNo">No</span>
                        </label>
                    </div>
                </div>
                
                <!-- Sexually Active Question -->
                <div class="mb-4">
                    <label class="block text-gray-700 font-medium mb-2" id="sexuallyActiveLabel">
                        <i class="fas fa-heart text-blue-500 mr-2"></i>Are you sexually active?
                    </label>
                    <div>
                        <label class="radio-option">
                            <input type="radio" name="sexuallyActive" value="yes">
                            <span id="sexuallyActiveYes">Yes</span>
                        </label>
                        <label class="radio-option">
                            <input type="radio" name="sexuallyActive" value="no" checked>
                            <span id="sexuallyActiveNo">No</span>
                        </label>
                    </div>
                </div>
            </div>
<!-- Alcohol Use Question -->
<div class="mb-4">
    <label class="block text-gray-700 font-medium mb-2" id="alcoholLabel">
        <i class="fas fa-wine-glass text-blue-500 mr-2"></i>Do you currently drink alcohol?
    </label>
    <div>
        <label class="radio-option">
            <input type="radio" name="alcohol" value="yes">
            <span id="alcoholYes">Yes</span>
        </label>
        <label class="radio-option">
            <input type="radio" name="alcohol" value="no" checked>
            <span id="alcoholNo">No</span>
        </label>
    </div>
</div>


            <div class="mt-6 text-center">
                <button id="checkButton" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-8 rounded-full transition duration-300 shadow-md">
                    <i class="fas fa-stethoscope mr-2"></i><span id="checkButtonText">Check Screenings</span>
                </button>
            </div>
        </div>

        <!-- Results Section (initially hidden) -->
        <div id="resultsSection" class="hidden">
            <div class="results-container bg-white rounded-xl shadow-lg p-6 mb-8">
                <h2 class="text-2xl font-bold text-blue-800 mb-4" id="resultsTitle">Your Recommended Screenings</h2>
                <div id="bmiResult" class="mb-4 p-3 bg-blue-50 rounded-lg hidden">
                    <p class="font-medium"><span id="bmiLabel">Your BMI:</span> <span id="bmiValue" class="font-bold"></span> - <span id="bmiCategory"></span></p>
                </div>
                <div id="screeningResults" class="space-y-4">
                    <!-- Results will be populated here -->
                </div>
            </div>
        </div>

        <!-- Doctor Discussion Tips -->
        <div id="doctorTipsSection" class="bg-blue-50 border-l-4 border-blue-500 rounded-lg shadow-md p-6 mb-8">
            <h3 class="text-xl font-bold text-blue-800 mb-3" id="tipsTitle">
                <i class="fas fa-comment-medical text-blue-600 mr-2"></i>Doctor Discussion Tips
            </h3>
            <ul class="space-y-2 text-gray-700" id="tipsList">
                <li class="flex items-start">
                    <span class="text-blue-500 mr-2 text-xl">📋</span>
                    <span id="tip1">Bring this checklist to your visit as a reference</span>
                </li>
                <li class="flex items-start">
                    <span class="text-blue-500 mr-2 text-xl">⏰</span>
                    <span id="tip2">Ask your doctor which screenings apply to you</span>
                </li>
                <li class="flex items-start">
                    <span class="text-blue-500 mr-2 text-xl">📆</span>
                    <span id="tip3">Review your past screenings with your doctor</span>
                </li>
            </ul>
        </div>

        <!-- USPSTF Grades Info Box -->
        <div id="uspstfGradesSection" class="bg-gradient-to-r from-blue-50 to-blue-100 rounded-lg shadow-md p-6 mb-8">
            <h3 class="text-xl font-bold text-blue-800 mb-3" id="gradesTitle">
                <i class="fas fa-info-circle text-blue-600 mr-2"></i>Understanding USPSTF Grades:
            </h3>
            <div class="grid md:grid-cols-2 gap-4">
                <div class="grade-item">
                    <div class="grade-icon grade-icon-a">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
                        </svg>
                    </div>
                    <div>
                        <div class="text-lg font-bold text-blue-800">Grade A</div>
                        <div id="gradeA" class="text-gray-700">Strongly Recommended</div>
                    </div>
                </div>
                <div class="grade-item">
                    <div class="grade-icon grade-icon-b">
                        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7" />
                        </svg>
                    </div>
                    <div>
                        <div class="text-lg font-bold text-blue-800">Grade B</div>
                        <div id="gradeB" class="text-gray-700">Recommended</div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Resources Section -->
        <div class="bg-white rounded-xl shadow-lg p-6 mb-8">
            <h3 class="text-xl font-bold text-blue-800 mb-4" id="resourcesTitle">
                <i class="fas fa-book-medical text-blue-600 mr-2"></i>Additional Resources
            </h3>
            <div class="grid md:grid-cols-2 gap-4">
                <a href="https://www.uspreventiveservicestaskforce.org/uspstf/recommendation-topics/uspstf-a-and-b-recommendations" target="_blank" class="flex items-center p-3 border border-blue-200 rounded-lg hover:bg-blue-50 transition duration-300">
                    <i class="fas fa-external-link-alt text-blue-500 mr-2"></i>
                    <span id="uspstfLink">USPSTF Recommendations</span>
                </a>
                <a href="https://www.cdc.gov/chronic-disease/prevention/preventive-care.html" target="_blank" class="flex items-center p-3 border border-blue-200 rounded-lg hover:bg-blue-50 transition duration-300">
                    <i class="fas fa-external-link-alt text-blue-500 mr-2"></i>
                    <span id="cdcLink">CDC Preventive Guidelines</span>
                </a>
            </div>
        </div>

        <!-- Disclaimer -->
        <div class="disclaimer mb-8" id="disclaimerSection">
            <p id="disclaimerText">This checklist is intended for educational purposes and does not replace professional medical advice. Talk to your healthcare provider to determine which screenings are right for you.</p>
        </div>

        <!-- Footer -->
        <footer class="text-center text-gray-500 text-sm py-4 no-print">
            <p id="footerText">This tool provides general guidance based on USPSTF recommendations. Always consult with your healthcare provider.</p>
        </footer>
    </div>

    <script>
        // Language translations
        const translations = {
            en: {
                mainTitle: "Adult Preventive Screening Checklist",
                mainSubtitle: "Find out which health screenings are recommended for you",
                tipsTitle: "Doctor Discussion Tips",
                tip1: "Bring this checklist to your visit as a reference",
                tip2: "Ask your doctor which screenings apply to you",
                tip3: "Review your past screenings with your doctor",
                ageLabel: "Enter your age:",
                sexLabel: "Select your sex assigned at birth:",
                selectOption: "Please select",
                maleOption: "Male (assigned at birth)",
                femaleOption: "Female (assigned at birth)",
                checkButtonText: "Check Screenings",
                resultsTitle: "Your Recommended Screenings",
                resourcesTitle: "Additional Resources",
                uspstfLink: "USPSTF Recommendations",
                cdcLink: "CDC Preventive Guidelines",
                footerText: "This tool provides general guidance based on USPSTF recommendations. Always consult with your healthcare provider.",
                gradesTitle: "Understanding USPSTF Grades:",
                gradeA: "Strongly Recommended",
                gradeB: "Recommended",
                disclaimerText: "This checklist is intended for educational purposes and does not replace professional medical advice. Talk to your healthcare provider to determine which screenings are right for you.",
                heightLabel: "Height:",
                weightLabel: "Weight:",
                feetText: "ft",
                inchesText: "in",
                poundsText: "lbs",
                additionalQuestionsTitle: "Additional Health Information",
                pregnantLabel: "Are you currently pregnant?",
                pregnantYes: "Yes",
                pregnantNo: "No",
                tobaccoLabel: "Have you ever used tobacco products?",
                tobaccoYes: "Yes",
                tobaccoNo: "No",
                sexuallyActiveLabel: "Are you sexually active?",
                sexuallyActiveYes: "Yes",
                sexuallyActiveNo: "No",
                alcoholLabel: "Do you currently drink alcohol?",
                alcoholYes: "Yes",
                alcoholNo: "No",
                bmiLabel: "Your BMI:",
                bmiUnderweight: "Underweight",
                bmiNormal: "Normal weight",
                bmiOverweight: "Overweight",
                bmiObese: "Obese"
            },
            es: {
                mainTitle: "Lista de Control de Exámenes Preventivos para Adultos",
                mainSubtitle: "Descubra qué exámenes de salud se recomiendan para usted",
                tipsTitle: "Consejos para Hablar con su Médico",
                tip1: "Lleve esta lista a su visita como referencia",
                tip2: "Pregunte a su médico qué exámenes se aplican a usted",
                tip3: "Revise sus exámenes anteriores con su médico",
                ageLabel: "Ingrese su edad:",
                sexLabel: "Seleccione su sexo asignado al nacer:",
                selectOption: "Por favor seleccione",
                maleOption: "Hombre (asignado al nacer)",
                femaleOption: "Mujer (asignada al nacer)",
                checkButtonText: "Verificar Exámenes",
                resultsTitle: "Sus Exámenes Recomendados",
                resourcesTitle: "Recursos Adicionales",
                uspstfLink: "Recomendaciones de USPSTF",
                cdcLink: "Guías Preventivas del CDC",
                footerText: "Esta herramienta proporciona orientación general basada en las recomendaciones de USPSTF. Siempre consulte con su proveedor de atención médica.",
                gradesTitle: "Entendiendo los Grados USPSTF:",
                gradeA: "Fuertemente Recomendado",
                gradeB: "Recomendado",
                disclaimerText: "Esta lista de verificación es solo para fines educativos y no reemplaza el consejo médico profesional. Hable con su proveedor de atención médica para determinar qué exámenes son adecuados para usted.",
                heightLabel: "Altura:",
                weightLabel: "Peso:",
                feetText: "pies",
                inchesText: "pulg",
                poundsText: "libras",
                additionalQuestionsTitle: "Información Adicional de Salud",
                pregnantLabel: "¿Está actualmente embarazada?",
                pregnantYes: "Sí",
                pregnantNo: "No",
                tobaccoLabel: "¿Ha usado productos de tabaco alguna vez?",
                tobaccoYes: "Sí",
                tobaccoNo: "No",
                sexuallyActiveLabel: "¿Es sexualmente activo/a?",
                sexuallyActiveYes: "Sí",
                sexuallyActiveNo: "No",
                alcoholLabel: "¿Actualmente consume alcohol?",
                alcoholYes: "Sí",
                alcoholNo: "No",
                bmiLabel: "Su IMC:",
                bmiUnderweight: "Bajo peso",
                bmiNormal: "Peso normal",
                bmiOverweight: "Sobrepeso",
                bmiObese: "Obesidad"
            },
            pt: {
                mainTitle: "Lista de Verificação de Exames Preventivos para Adultos",
                mainSubtitle: "Descubra quais exames de saúde são recomendados para você",
                tipsTitle: "Dicas para Conversar com seu Médico",
                tip1: "Leve esta lista para sua consulta como referência",
                tip2: "Pergunte ao seu médico quais exames se aplicam a você",
                tip3: "Revise seus exames anteriores com seu médico",
                ageLabel: "Digite sua idade:",
                sexLabel: "Selecione seu sexo atribuído ao nascer:",
                selectOption: "Por favor selecione",
                maleOption: "Homem (atribuído ao nascer)",
                femaleOption: "Mulher (atribuída ao nascer)",
                checkButtonText: "Verificar Exames",
                resultsTitle: "Seus Exames Recomendados",
                resourcesTitle: "Recursos Adicionais",
                uspstfLink: "Recomendações da USPSTF",
                cdcLink: "Diretrizes Preventivas do CDC",
                footerText: "Esta ferramenta fornece orientação geral com base nas recomendações da USPSTF. Sempre consulte seu profissional de saúde.",
                gradesTitle: "Entendendo os Graus USPSTF:",
                gradeA: "Fortemente Recomendado",
                gradeB: "Recomendado",
                disclaimerText: "Esta lista de verificação é destinada apenas para fins educacionais e não substitui o aconselhamento médico profissional. Converse com seu profissional de saúde para determinar quais exames são adequados para você.",
                heightLabel: "Altura:",
                weightLabel: "Peso:",
                feetText: "pés",
                inchesText: "pol",
                poundsText: "libras",
                additionalQuestionsTitle: "Informações Adicionais de Saúde",
                pregnantLabel: "Você está grávida atualmente?",
                pregnantYes: "Sim",
                pregnantNo: "Não",
                tobaccoLabel: "Você já usou produtos de tabaco?",
                tobaccoYes: "Sim",
                tobaccoNo: "Não",
                sexuallyActiveLabel: "Você é sexualmente ativo/a?",
                sexuallyActiveYes: "Sim",
                sexuallyActiveNo: "Não",
                alcoholLabel: "Você atualmente consome álcool?",
                alcoholYes: "Sim",
                alcoholNo: "Não",
                bmiLabel: "Seu IMC:",
                bmiUnderweight: "Abaixo do peso",
                bmiNormal: "Peso normal",
                bmiOverweight: "Sobrepeso",
                bmiObese: "Obesidade"
            }
        };

        // Updated Screening database with more precise USPSTF A&B recommendations
        const screenings = {
            general: [
                { 
                    name: "Blood Pressure Screening", 
                    frequency: "Every year", 
                    grade: "A", 
                    minAge: 18, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Checks your blood pressure to find problems early.",
                    recommendedAge: "18+ years",
                    icon: "❤️",
                    whyItMatters: "Early treatment helps prevent heart disease, stroke, and kidney problems.",
                    eligibility: "All adults"
                },
                { 
                    name: "Cholesterol Screening", 
                    frequency: "Every 4-6 years", 
                    grade: "B", 
                    minAge: 20, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Checks the fats in your blood that can affect your heart.",
                    recommendedAge: "20+ years",
                    icon: "🩸",
                    whyItMatters: "Finding high cholesterol early helps protect your heart and prevent heart attacks.",
                    eligibility: "Adults aged 20 and older, especially those at risk for heart disease"
                },
                { 
                    name: "Diabetes Screening", 
                    frequency: "Every 3 years", 
                    grade: "B", 
                    minAge: 35, 
                    maxAge: 70, 
                    sex: "all",
                    explanation: "Checks your blood sugar to find diabetes early.",
                    recommendedAge: "35-70 years",
                    icon: "🧪",
                    whyItMatters: "Early detection prevents serious complications like heart, kidney, and eye problems.",
                    eligibility: "Adults who are overweight or obese",
                    bmiRequired: 25
                },
                { 
                    name: "Colorectal Cancer Screening", 
                    frequency: "Every 1-10 years depending on test type", 
                    grade: "A", 
                    minAge: 45, 
                    maxAge: 75, 
                    sex: "all",
                    explanation: "Looks for signs of cancer in your colon or rectum.",
                    recommendedAge: "45-75 years",
                    icon: "🔍",
                    whyItMatters: "Finding polyps early can prevent cancer or catch it when it's most treatable.",
                    eligibility: "All adults in this age range",
                    talkWithDoctor: true
                },
                { 
                    name: "Depression Screening", 
                    frequency: "At regular visits", 
                    grade: "B", 
                    minAge: 18, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Checks for signs of depression using brief screening questions.",
                    recommendedAge: "18+ years",
                    icon: "🧠",
                    whyItMatters: "Getting help early can improve your mood, relationships, and quality of life.",
                    eligibility: "All adults"
                },
                { 
                    name: "Hepatitis C Screening", 
                    frequency: "Once in a lifetime", 
                    grade: "B", 
                    minAge: 18, 
                    maxAge: 79, 
                    sex: "all",
                    explanation: "Tests for a liver infection that often has no symptoms.",
                    recommendedAge: "18-79 years",
                    icon: "🔬",
                    whyItMatters: "Early treatment can prevent liver damage, cirrhosis, and liver cancer.",
                    eligibility: "All adults aged 18-79, including those with risk factors"
                },
                { 
                    name: "Lung Cancer Screening", 
                    frequency: "Every year", 
                    grade: "B", 
                    minAge: 50, 
                    maxAge: 80, 
                    sex: "all", 
                    explanation: "Uses a low-dose CT scan to find lung cancer early.",
                    recommendedAge: "50-80 years",
                    icon: "🫁",
                    whyItMatters: "Catching lung cancer early greatly improves the chance of successful treatment.",
                    eligibility: "Current or former smoker with 20+ pack-year history who quit within the last 15 years",
                    requireTobacco: true,
                    talkWithDoctor: true
                },
                { 
                    name: "Obesity Screening and Counseling", 
                    frequency: "At regular visits", 
                    grade: "B", 
                    minAge: 18, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Measures BMI and offers counseling for those with obesity.",
                    recommendedAge: "18+ years",
                    icon: "⚖️",
                    whyItMatters: "Weight management can reduce risk of heart disease, diabetes, and other conditions.",
                    eligibility: "Adults with BMI of 30 or higher",
                    bmiRequired: 30
                },
                { 
                    name: "HIV Screening", 
                    frequency: "At least once, more often with risk factors", 
                    grade: "A", 
                    minAge: 15, 
                    maxAge: 65, 
                    sex: "all",
                    explanation: "Tests for HIV infection, which can be present without symptoms for years.",
                    recommendedAge: "15-65 years",
                    icon: "🧬",
                    whyItMatters: "Early detection allows for effective treatment and prevents transmission to others.",
                    eligibility: "All adults in this age range"
                },
                { 
                    name: "Tobacco Use Screening and Counseling", 
                    frequency: "At regular visits", 
                    grade: "A", 
                    minAge: 18, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Identifies tobacco users and provides interventions to help quit.",
                    recommendedAge: "18+ years",
                    icon: "🚭",
                    whyItMatters: "Quitting tobacco reduces risk of cancer, heart disease, and lung disease.",
                    eligibility: "Current tobacco users",
                    requireTobacco: true
                },
                { 
                    name: "Unhealthy Alcohol Use Screening", 
                    frequency: "At regular visits", 
                    grade: "B", 
                    minAge: 18, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Screens for risky drinking patterns and provides brief counseling.",
                    recommendedAge: "18+ years",
                    icon: "🍷",
                    whyItMatters: "Reducing excessive alcohol use can prevent liver disease, injuries, and other health problems.",
                    eligibility: "All adults"
                },
                { 
                    name: "Chlamydia and Gonorrhea Screening", 
                    frequency: "Annually or as recommended", 
                    grade: "B", 
                    minAge: 18, 
                    maxAge: 24, 
                    sex: "female",
                    explanation: "Tests for common sexually transmitted infections that often have no symptoms.",
                    recommendedAge: "Sexually active women under 25",
                    icon: "🔬",
                    whyItMatters: "Early detection and treatment prevents complications like pelvic inflammatory disease and infertility.",
                    eligibility: "Sexually active women under 25 and older women at increased risk",
                    requireSexuallyActive: true
                },
                { 
                    name: "Syphilis Screening", 
                    frequency: "At least once, more often with risk factors", 
                    grade: "A", 
                    minAge: 18, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Tests for syphilis infection, which can cause serious health problems if untreated.",
                    recommendedAge: "18+ years",
                    icon: "🔬",
                    whyItMatters: "Early detection and treatment prevents serious complications affecting the heart, brain, and other organs.",
                    eligibility: "Adults at increased risk",
                    requireSexuallyActive: true
                },
                { 
                    name: "Diet Counseling", 
                    frequency: "As needed", 
                    grade: "B", 
                    minAge: 18, 
                    maxAge: 120, 
                    sex: "all",
                    explanation: "Provides personalized advice on healthy eating patterns.",
                    recommendedAge: "18+ years",
                    icon: "🥗",
                    whyItMatters: "Healthy eating can reduce risk of heart disease, diabetes, and other chronic conditions.",
                    eligibility: "Adults with cardiovascular risk factors or elevated BMI",
                    bmiRequired: 25
                }
            ],
            female: [
                { 
                    name: "Breast Cancer Screening (Mammogram)", 
                    frequency: "Every 2 years", 
                    grade: "B", 
                    minAge: 50, 
                    maxAge: 74, 
                    sex: "female",
                    explanation: "Uses X-rays to detect breast cancer before you can feel a lump.",
                    recommendedAge: "50-74 years",
                    icon: "🎀",
                    whyItMatters: "Detecting breast cancer early gives you more treatment options and better outcomes.",
                    eligibility: "Women with average risk",
                    talkWithDoctor: true
                },
                { 
                    name: "Cervical Cancer Screening", 
                    frequency: "Every 3 years (Pap test) or every 5 years with HPV test or co-testing", 
                    grade: "A", 
                    minAge: 21, 
                    maxAge: 65, 
                    sex: "female",
                    explanation: "Checks for abnormal cells in the cervix that could become cancer.",
                    recommendedAge: "21-65 years",
                    icon: "👩‍⚕️",
                    whyItMatters: "Regular screening prevents most cervical cancers and saves lives.",
                    eligibility: "Anyone with a cervix (typically women ages 21-65)"
                },
                { 
                    name: "Osteoporosis Screening", 
                    frequency: "Once, then as recommended by your doctor", 
                    grade: "B", 
                    minAge: 65, 
                    maxAge: 120, 
                    sex: "female",
                    explanation: "Measures bone density to detect thinning bones.",
                    recommendedAge: "65+ years",
                    icon: "🦴",
                    whyItMatters: "Finding weak bones early helps prevent fractures and maintain independence.",
                    eligibility: "Women age 65 and older, and younger women at increased risk"
                },
                { 
                    name: "Prenatal Care and Screenings", 
                    frequency: "Throughout pregnancy", 
                    grade: "A", 
                    minAge: 13, 
                    maxAge: 55, 
                    sex: "female",
                    explanation: "Regular check-ups and tests to monitor your health and your baby's development.",
                    recommendedAge: "During pregnancy",
                    icon: "👶",
                    whyItMatters: "Helps ensure a healthy pregnancy and reduces risks of complications.",
                    eligibility: "Pregnant women",
                    requirePregnant: true
                },
                { 
                    name: "Preeclampsia Prevention", 
                    frequency: "Daily low-dose aspirin after 12 weeks of pregnancy", 
                    grade: "B", 
                    minAge: 13, 
                    maxAge: 55, 
                    sex: "female",
                    explanation: "Low-dose aspirin to prevent preeclampsia in high-risk pregnancies.",
                    recommendedAge: "During pregnancy",
                    icon: "💊",
                    whyItMatters: "Reduces risk of preeclampsia, a serious pregnancy complication affecting mother and baby.",
                    eligibility: "Pregnant women at high risk for preeclampsia",
                    requirePregnant: true,
                    talkWithDoctor: true
                },
                { 
                    name: "Gestational Diabetes Screening", 
                    frequency: "At 24-28 weeks of pregnancy", 
                    grade: "B", 
                    minAge: 13, 
                    maxAge: 55, 
                    sex: "female",
                    explanation: "Tests for diabetes that develops during pregnancy.",
                    recommendedAge: "During pregnancy",
                    icon: "🧪",
                    whyItMatters: "Early detection and management reduces complications for mother and baby.",
                    eligibility: "Pregnant women after 24 weeks",
                    requirePregnant: true
                },
                { 
                    name: "Hepatitis B Screening", 
                    frequency: "At first prenatal visit", 
                    grade: "A", 
                    minAge: 13, 
                    maxAge: 55, 
                    sex: "female",
                    explanation: "Tests for hepatitis B infection, which can be passed to the baby.",
                    recommendedAge: "During pregnancy",
                    icon: "🔬",
                    whyItMatters: "Early detection allows for interventions to prevent transmission to the baby.",
                    eligibility: "All pregnant women",
                    requirePregnant: true
                },
                { 
                    name: "Intimate Partner Violence Screening", 
                    frequency: "At regular visits", 
                    grade: "B", 
                    minAge: 18, 
                    maxAge: 50, 
                    sex: "female",
                    explanation: "Screens for domestic violence and provides support resources.",
                    recommendedAge: "18-50 years",
                    icon: "🛡️",
                    whyItMatters: "Identifies those at risk and connects them with support services.",
                    eligibility: "Women of reproductive age"
                }
            ],
            male: [
                { 
                    name: "Abdominal Aortic Aneurysm Screening", 
                    frequency: "Once in a lifetime", 
                    grade: "B", 
                    minAge: 65, 
                    maxAge: 75, 
                    sex: "male", 
                    explanation: "Uses ultrasound to check for a dangerous bulge in your main blood vessel.",
                    recommendedAge: "65-75 years",
                    icon: "🔍",
                    whyItMatters: "Finding an aneurysm before it bursts can save your life.",
                    eligibility: "Men who have ever smoked (at least 100 cigarettes in their lifetime)",
                    requireTobacco: true
                },
                { 
                    name: "Prostate Cancer Screening Discussion", 
                    frequency: "As decided with your doctor", 
                    grade: "B", 
                    minAge: 55, 
                    maxAge: 69, 
                    sex: "male",
                    explanation: "A conversation with your doctor about PSA testing benefits and risks.",
                    recommendedAge: "55-69 years",
                    icon: "🗣️",
                    whyItMatters: "Helps you make an informed decision about prostate screening.",
                    eligibility: "Men in this age range",
                    talkWithDoctor: true
                }
            ]
        };

        // Translations for screenings
        const screeningTranslations = {
            es: {
                "Blood Pressure Screening": {
                    name: "Examen de Presión Arterial",
                    frequency: "Cada año",
                    explanation: "Revisa su presión arterial para encontrar problemas temprano.",
                    recommendedAge: "18+ años",
                    whyItMatters: "El tratamiento temprano ayuda a prevenir enfermedades cardíacas, derrames cerebrales y problemas renales.",
                    eligibility: "Todos los adultos"
                },
                "Cholesterol Screening": {
                    name: "Examen de Colesterol",
                    frequency: "Cada 4-6 años",
                    explanation: "Revisa las grasas en su sangre que pueden afectar su corazón.",
                    recommendedAge: "20+ años",
                    whyItMatters: "Encontrar colesterol alto temprano ayuda a proteger su corazón y prevenir ataques cardíacos.",
                    eligibility: "Adultos de 20 años o más, especialmente aquellos con riesgo de enfermedad cardíaca"
                },
                "Diabetes Screening": {
                    name: "Examen de Diabetes",
                    frequency: "Cada 3 años",
                    explanation: "Revisa su azúcar en sangre para encontrar diabetes temprano.",
                    recommendedAge: "35-70 años",
                    whyItMatters: "La detección temprana previene complicaciones graves como problemas cardíacos, renales y oculares.",
                    eligibility: "Adultos con sobrepeso u obesidad"
                },
                "Colorectal Cancer Screening": {
                    name: "Examen de Cáncer Colorrectal",
                    frequency: "Cada 1-10 años dependiendo del tipo de prueba",
                    explanation: "Busca signos de cáncer en su colon o recto.",
                    recommendedAge: "45-75 años",
                    whyItMatters: "Encontrar pólipos temprano puede prevenir el cáncer o detectarlo cuando es más tratable.",
                    eligibility: "Todos los adultos en este rango de edad",
                    talkWithDoctor: "Existen diferentes opciones de prueba disponibles."
                },
                "Depression Screening": {
                    name: "Examen de Depresión",
                    frequency: "En visitas regulares",
                    explanation: "Verifica signos de depresión usando preguntas breves de detección.",
                    recommendedAge: "18+ años",
                    whyItMatters: "Obtener ayuda temprano puede mejorar su estado de ánimo, relaciones y calidad de vida.",
                    eligibility: "Todos los adultos"
                },
                "Hepatitis C Screening": {
                    name: "Examen de Hepatitis C",
                    frequency: "Una vez en la vida",
                    explanation: "Prueba para una infección hepática que a menudo no tiene síntomas.",
                    recommendedAge: "18-79 años",
                    whyItMatters: "El tratamiento temprano puede prevenir daño hepático, cirrosis y cáncer de hígado.",
                    eligibility: "Todos los adultos de 18-79 años, incluyendo aquellos con factores de riesgo"
                },
                "Lung Cancer Screening": {
                    name: "Examen de Cáncer de Pulmón",
                    frequency: "Cada año",
                    explanation: "Utiliza una tomografía computarizada de baja dosis para encontrar cáncer de pulmón temprano.",
                    recommendedAge: "50-80 años",
                    whyItMatters: "Detectar el cáncer de pulmón temprano mejora enormemente la posibilidad de un tratamiento exitoso.",
                    eligibility: "Fumador actual o anterior con historial de 20+ paquetes-año que dejó de fumar en los últimos 15 años",
                    talkWithDoctor: "Este examen es solo para personas con historial de tabaquismo significativo."
                },
                "Breast Cancer Screening (Mammogram)": {
                    name: "Examen de Cáncer de Mama (Mamografía)",
                    frequency: "Cada 2 años",
                    explanation: "Utiliza rayos X para detectar cáncer de mama antes de que pueda sentir un bulto.",
                    recommendedAge: "50-74 años",
                    whyItMatters: "Detectar el cáncer de mama temprano le da más opciones de tratamiento y mejores resultados.",
                    eligibility: "Mujeres con riesgo promedio",
                    talkWithDoctor: "Hable con su médico: Las mujeres con antecedentes familiares pueden necesitar comenzar antes."
                },
                "Cervical Cancer Screening": {
                    name: "Examen de Cáncer Cervical",
                    frequency: "Cada 3 años (prueba de Papanicolaou) o cada 5 años con prueba de VPH o co-prueba",
                    explanation: "Verifica células anormales en el cuello uterino que podrían convertirse en cáncer.",
                    recommendedAge: "21-65 años",
                    whyItMatters: "El examen regular previene la mayoría de los cánceres cervicales y salva vidas.",
                    eligibility: "Cualquier persona con cuello uterino (típicamente mujeres de 21-65 años)"
                },
                "Osteoporosis Screening": {
                    name: "Examen de Osteoporosis",
                    frequency: "Una vez, luego según lo recomendado por su médico",
                    explanation: "Mide la densidad ósea para detectar huesos debilitados.",
                    recommendedAge: "65+ años",
                    whyItMatters: "Encontrar huesos débiles temprano ayuda a prevenir fracturas y mantener la independencia.",
                    eligibility: "Mujeres de 65 años o más, y mujeres más jóvenes con mayor riesgo"
                },
                "Abdominal Aortic Aneurysm Screening": {
                    name: "Examen de Aneurisma Aórtico Abdominal",
                    frequency: "Una vez en la vida",
                    explanation: "Utiliza ultrasonido para verificar una protuberancia peligrosa en su vaso sanguíneo principal.",
                    recommendedAge: "65-75 años",
                    whyItMatters: "Encontrar un aneurisma antes de que se rompa puede salvar su vida.",
                    eligibility: "Hombres que alguna vez han fumado (al menos 100 cigarrillos en su vida)"
                },
                "Prostate Cancer Screening Discussion": {
                    name: "Discusión sobre Examen de Cáncer de Próstata",
                    frequency: "Según lo decidido con su médico",
                    explanation: "Una conversación con su médico sobre los beneficios y riesgos de la prueba PSA.",
                    recommendedAge: "55-69 años",
                    whyItMatters: "Le ayuda a tomar una decisión informada sobre el examen de próstata.",
                    eligibility: "Hombres en este rango de edad",
                    talkWithDoctor: "Los beneficios y riesgos deben discutirse antes de realizar la prueba."
                },
                "Obesity Screening and Counseling": {
                    name: "Examen y Consejería de Obesidad",
                    frequency: "En visitas regulares",
                    explanation: "Mide el IMC y ofrece consejería para aquellos con obesidad.",
                    recommendedAge: "18+ años",
                    whyItMatters: "El manejo del peso puede reducir el riesgo de enfermedades cardíacas, diabetes y otras condiciones.",
                    eligibility: "Adultos con IMC de 30 o superior"
                },
                "HIV Screening": {
                    name: "Prueba de VIH",
                    frequency: "Al menos una vez, más a menudo con factores de riesgo",
                    explanation: "Prueba para la infección por VIH, que puede estar presente sin síntomas durante años.",
                    recommendedAge: "15-65 años",
                    whyItMatters: "La detección temprana permite un tratamiento efectivo y previene la transmisión a otros.",
                    eligibility: "Todos los adultos en este rango de edad"
                },
                "Tobacco Use Screening and Counseling": {
                    name: "Detección y Consejería sobre Uso de Tabaco",
                    frequency: "En visitas regulares",
                    explanation: "Identifica a los usuarios de tabaco y proporciona intervenciones para ayudar a dejar de fumar.",
                    recommendedAge: "18+ años",
                    whyItMatters: "Dejar el tabaco reduce el riesgo de cáncer, enfermedades cardíacas y enfermedades pulmonares.",
                    eligibility: "Usuarios actuales de tabaco"
                },
                "Unhealthy Alcohol Use Screening": {
                    name: "Detección de Consumo Nocivo de Alcohol",
                    frequency: "En visitas regulares",
                    explanation: "Evalúa patrones de consumo riesgoso de alcohol y proporciona consejería breve.",
                    recommendedAge: "18+ años",
                    whyItMatters: "Reducir el consumo excesivo de alcohol puede prevenir enfermedades hepáticas, lesiones y otros problemas de salud.",
                    eligibility: "Todos los adultos"
                },
                "Chlamydia and Gonorrhea Screening": {
                    name: "Prueba de Clamidia y Gonorrea",
                    frequency: "Anualmente o según recomendación",
                    explanation: "Pruebas para infecciones de transmisión sexual comunes que a menudo no tienen síntomas.",
                    recommendedAge: "Mujeres sexualmente activas menores de 25 años",
                    whyItMatters: "La detección y tratamiento tempranos previenen complicaciones como la enfermedad inflamatoria pélvica y la infertilidad.",
                    eligibility: "Mujeres sexualmente activas menores de 25 años y mujeres mayores con mayor riesgo"
                },
                "Syphilis Screening": {
                    name: "Prueba de Sífilis",
                    frequency: "Al menos una vez, más a menudo con factores de riesgo",
                    explanation: "Prueba para la infección por sífilis, que puede causar graves problemas de salud si no se trata.",
                    recommendedAge: "18+ años",
                    whyItMatters: "La detección y tratamiento tempranos previenen complicaciones graves que afectan al corazón, cerebro y otros órganos.",
                    eligibility: "Adultos con mayor riesgo"
                },
                "Diet Counseling": {
                    name: "Consejería Dietética",
                    frequency: "Según sea necesario",
                    explanation: "Proporciona consejos personalizados sobre patrones de alimentación saludable.",
                    recommendedAge: "18+ años",
                    whyItMatters: "Una alimentación saludable puede reducir el riesgo de enfermedades cardíacas, diabetes y otras condiciones crónicas.",
                    eligibility: "Adultos con factores de riesgo cardiovascular o IMC elevado"
                },
                "Prenatal Care and Screenings": {
                    name: "Atención Prenatal y Exámenes",
                    frequency: "Durante todo el embarazo",
                    explanation: "Chequeos y pruebas regulares para monitorear su salud y el desarrollo de su bebé.",
                    recommendedAge: "Durante el embarazo",
                    whyItMatters: "Ayuda a asegurar un embarazo saludable y reduce los riesgos de complicaciones.",
                    eligibility: "Mujeres embarazadas"
                },
                "Preeclampsia Prevention": {
                    name: "Prevención de Preeclampsia",
                    frequency: "Aspirina diaria en dosis baja después de 12 semanas de embarazo",
                    explanation: "Aspirina en dosis baja para prevenir la preeclampsia en embarazos de alto riesgo.",
                    recommendedAge: "Durante el embarazo",
                    whyItMatters: "Reduce el riesgo de preeclampsia, una complicación grave del embarazo que afecta a la madre y al bebé.",
                    eligibility: "Mujeres embarazadas con alto riesgo de preeclampsia",
                    talkWithDoctor: "Este tratamiento preventivo es solo para embarazos de alto riesgo."
                },
                "Gestational Diabetes Screening": {
                    name: "Prueba de Diabetes Gestacional",
                    frequency: "A las 24-28 semanas de embarazo",
                    explanation: "Prueba para la diabetes que se desarrolla durante el embarazo.",
                    recommendedAge: "Durante el embarazo",
                    whyItMatters: "La detección y manejo tempranos reducen las complicaciones para la madre y el bebé.",
                    eligibility: "Mujeres embarazadas después de 24 semanas"
                },
                "Hepatitis B Screening": {
                    name: "Prueba de Hepatitis B",
                    frequency: "En la primera visita prenatal",
                    explanation: "Prueba para la infección por hepatitis B, que puede transmitirse al bebé.",
                    recommendedAge: "Durante el embarazo",
                    whyItMatters: "La detección temprana permite intervenciones para prevenir la transmisión al bebé.",
                    eligibility: "Todas las mujeres embarazadas"
                },
                "Intimate Partner Violence Screening": {
                    name: "Detección de Violencia de Pareja",
                    frequency: "En visitas regulares",
                    explanation: "Evalúa la violencia doméstica y proporciona recursos de apoyo.",
                    recommendedAge: "18-50 años",
                    whyItMatters: "Identifica a las personas en riesgo y las conecta con servicios de apoyo.",
                    eligibility: "Mujeres en edad reproductiva"
                }
            },
            pt: {
                "Blood Pressure Screening": {
                    name: "Exame de Pressão Arterial",
                    frequency: "Todos os anos",
                    explanation: "Verifica sua pressão arterial para encontrar problemas cedo.",
                    recommendedAge: "18+ anos",
                    whyItMatters: "O tratamento precoce ajuda a prevenir doenças cardíacas, derrames e problemas renais.",
                    eligibility: "Todos os adultos"
                },
                "Cholesterol Screening": {
                    name: "Exame de Colesterol",
                    frequency: "A cada 4-6 anos",
                    explanation: "Verifica as gorduras no seu sangue que podem afetar seu coração.",
                    recommendedAge: "20+ anos",
                    whyItMatters: "Encontrar colesterol alto cedo ajuda a proteger seu coração e prevenir ataques cardíacos.",
                    eligibility: "Adultos com 20 anos ou mais, especialmente aqueles com risco de doença cardíaca"
                },
                "Diabetes Screening": {
                    name: "Exame de Diabetes",
                    frequency: "A cada 3 anos",
                    explanation: "Verifica seu açúcar no sangue para encontrar diabetes cedo.",
                    recommendedAge: "35-70 anos",
                    whyItMatters: "A detecção precoce previne complicações graves como problemas cardíacos, renais e oculares.",
                    eligibility: "Adultos com sobrepeso ou obesidade"
                },
                "Colorectal Cancer Screening": {
                    name: "Exame de Câncer Colorretal",
                    frequency: "A cada 1-10 anos dependendo do tipo de teste",
                    explanation: "Procura sinais de câncer no seu cólon ou reto.",
                    recommendedAge: "45-75 anos",
                    whyItMatters: "Encontrar pólipos cedo pode prevenir o câncer ou detectá-lo quando é mais tratável.",
                    eligibility: "Todos os adultos nesta faixa etária",
                    talkWithDoctor: "Converse com seu médico: Existem diferentes opções de teste disponíveis."
                },
                "Depression Screening": {
                    name: "Exame de Depressão",
                    frequency: "Em consultas regulares",
                    explanation: "Verifica sinais de depressão usando perguntas breves de triagem.",
                    recommendedAge: "18+ anos",
                    whyItMatters: "Obter ajuda cedo pode melhorar seu humor, relacionamentos e qualidade de vida.",
                    eligibility: "Todos os adultos"
                },
                "Hepatitis C Screening": {
                    name: "Exame de Hepatite C",
                    frequency: "Uma vez na vida",
                    explanation: "Testa uma infecção hepática que muitas vezes não tem sintomas.",
                    recommendedAge: "18-79 anos",
                    whyItMatters: "O tratamento precoce pode prevenir danos hepáticos, cirrose e câncer de fígado.",
                    eligibility: "Todos os adultos de 18-79 anos, incluindo aqueles com fatores de risco"
                },
                "Lung Cancer Screening": {
                    name: "Exame de Câncer de Pulmão",
                    frequency: "Todos os anos",
                    explanation: "Usa uma tomografia computadorizada de baixa dose para encontrar câncer de pulmão cedo.",
                    recommendedAge: "50-80 anos",
                    whyItMatters: "Detectar o câncer de pulmão cedo melhora enormemente a chance de um tratamento bem-sucedido.",
                    eligibility: "Fumante atual ou ex-fumante com histórico de 20+ maços-ano que parou de fumar nos últimos 15 anos",
                    talkWithDoctor: "Converse com seu médico: Este exame é apenas para pessoas com histórico significativo de tabagismo."
                },
                "Breast Cancer Screening (Mammogram)": {
                    name: "Exame de Câncer de Mama (Mamografia)",
                    frequency: "A cada 2 anos",
                    explanation: "Usa raios-X para detectar câncer de mama antes que você possa sentir um caroço.",
                    recommendedAge: "50-74 anos",
                    whyItMatters: "Detectar o câncer de mama cedo dá mais opções de tratamento e melhores resultados.",
                    eligibility: "Mulheres com risco médio",
                    talkWithDoctor: "Converse com seu médico: Mulheres com histórico familiar podem precisar começar mais cedo."
                },
                "Cervical Cancer Screening": {
                    name: "Exame de Câncer Cervical",
                    frequency: "A cada 3 anos (teste Papanicolau) ou a cada 5 anos com teste HPV ou co-teste",
                    explanation: "Verifica células anormais no colo do útero que poderiam se tornar câncer.",
                    recommendedAge: "21-65 anos",
                    whyItMatters: "O exame regular previne a maioria dos cânceres cervicais e salva vidas.",
                    eligibility: "Qualquer pessoa com colo do útero (tipicamente mulheres de 21-65 anos)"
                },
                "Osteoporosis Screening": {
                    name: "Exame de Osteoporose",
                    frequency: "Uma vez, depois conforme recomendado pelo seu médico",
                    explanation: "Mede a densidade óssea para detectar ossos enfraquecidos.",
                    recommendedAge: "65+ anos",
                    whyItMatters: "Encontrar ossos fracos cedo ajuda a prevenir fraturas e manter a independência.",
                    eligibility: "Mulheres com 65 anos ou mais, e mulheres mais jovens com maior risco"
                },
                "Abdominal Aortic Aneurysm Screening": {
                    name: "Exame de Aneurisma Aórtico Abdominal",
                    frequency: "Uma vez na vida",
                    explanation: "Usa ultrassom para verificar uma dilatação perigosa em seu vaso sanguíneo principal.",
                    recommendedAge: "65-75 anos",
                    whyItMatters: "Encontrar um aneurisma antes que se rompa pode salvar sua vida.",
                    eligibility: "Homens que já fumaram (pelo menos 100 cigarros na vida)"
                },
                "Prostate Cancer Screening Discussion": {
                    name: "Discussão sobre Exame de Câncer de Próstata",
                    frequency: "Conforme decidido com seu médico",
                    explanation: "Uma conversa com seu médico sobre os benefícios e riscos do teste PSA.",
                    recommendedAge: "55-69 anos",
                    whyItMatters: "Ajuda você a tomar uma decisão informada sobre o exame de próstata.",
                    eligibility: "Homens nesta faixa etária",
                    talkWithDoctor: "Converse com seu médico: Os benefícios e riscos devem ser discutidos antes de realizar o teste."
                },
                "Obesity Screening and Counseling": {
                    name: "Exame e Aconselhamento de Obesidade",
                    frequency: "Em consultas regulares",
                    explanation: "Mede o IMC e oferece aconselhamento para aqueles com obesidade.",
                    recommendedAge: "18+ anos",
                    whyItMatters: "O gerenciamento do peso pode reduzir o risco de doenças cardíacas, diabetes e outras condições.",
                    eligibility: "Adultos com IMC de 30 ou superior"
                },
                "HIV Screening": {
                    name: "Teste de HIV",
                    frequency: "Pelo menos uma vez, mais frequentemente com fatores de risco",
                    explanation: "Testa a infecção por HIV, que pode estar presente sem sintomas por anos.",
                    recommendedAge: "15-65 anos",
                    whyItMatters: "A detecção precoce permite tratamento eficaz e previne a transmissão para outros.",
                    eligibility: "Todos os adultos nesta faixa etária"
                },
                "Tobacco Use Screening and Counseling": {
                    name: "Triagem e Aconselhamento sobre Uso de Tabaco",
                    frequency: "Em consultas regulares",
                    explanation: "Identifica usuários de tabaco e fornece intervenções para ajudar a parar.",
                    recommendedAge: "18+ anos",
                    whyItMatters: "Parar de fumar reduz o risco de câncer, doenças cardíacas e doenças pulmonares.",
                    eligibility: "Usuários atuais de tabaco"
                },
                "Unhealthy Alcohol Use Screening": {
                    name: "Triagem de Uso Prejudicial de Álcool",
                    frequency: "Em consultas regulares",
                    explanation: "Avalia padrões de consumo arriscado de álcool e fornece aconselhamento breve.",
                    recommendedAge: "18+ anos",
                    whyItMatters: "Reduzir o uso excessivo de álcool pode prevenir doenças hepáticas, lesões e outros problemas de saúde.",
                    eligibility: "Todos os adultos"
                },
                "Chlamydia and Gonorrhea Screening": {
                    name: "Teste de Clamídia e Gonorreia",
                    frequency: "Anualmente ou conforme recomendado",
                    explanation: "Testes para infecções sexualmente transmissíveis comuns que frequentemente não têm sintomas.",
                    recommendedAge: "Mulheres sexualmente ativas com menos de 25 anos",
                    whyItMatters: "A detecção e tratamento precoces previnem complicações como doença inflamatória pélvica e infertilidade.",
                    eligibility: "Mulheres sexualmente ativas com menos de 25 anos e mulheres mais velhas com risco aumentado"
                },
                "Syphilis Screening": {
                    name: "Teste de Sífilis",
                    frequency: "Pelo menos uma vez, mais frequentemente com fatores de risco",
                    explanation: "Testa a infecção por sífilis, que pode causar sérios problemas de saúde se não tratada.",
                    recommendedAge: "18+ anos",
                    whyItMatters: "A detecção e tratamento precoces previnem complicações graves afetando o coração, cérebro e outros órgãos.",
                    eligibility: "Adultos com risco aumentado"
                },
                "Diet Counseling": {
                    name: "Aconselhamento Dietético",
                    frequency: "Conforme necessário",
                    explanation: "Fornece conselhos personalizados sobre padrões alimentares saudáveis.",
                    recommendedAge: "18+ anos",
                    whyItMatters: "Alimentação saudável pode reduzir o risco de doenças cardíacas, diabetes e outras condições crônicas.",
                    eligibility: "Adultos com fatores de risco cardiovascular ou IMC elevado"
                },
                "Prenatal Care and Screenings": {
                    name: "Cuidados Pré-natais e Exames",
                    frequency: "Durante toda a gravidez",
                    explanation: "Check-ups e testes regulares para monitorar sua saúde e o desenvolvimento do seu bebê.",
                    recommendedAge: "Durante a gravidez",
                    whyItMatters: "Ajuda a garantir uma gravidez saudável e reduz os riscos de complicações.",
                    eligibility: "Mulheres grávidas"
                },
                "Preeclampsia Prevention": {
                    name: "Prevenção de Pré-eclâmpsia",
                    frequency: "Aspirina diária em baixa dose após 12 semanas de gravidez",
                    explanation: "Aspirina em baixa dose para prevenir pré-eclâmpsia em gravidezes de alto risco.",
                    recommendedAge: "Durante a gravidez",
                    whyItMatters: "Reduz o risco de pré-eclâmpsia, uma complicação grave da gravidez que afeta a mãe e o bebê.",
                    eligibility: "Mulheres grávidas com alto risco de pré-eclâmpsia",
                    talkWithDoctor: "Converse com seu médico: Este tratamento preventivo é apenas para gravidezes de alto risco."
                },
                "Gestational Diabetes Screening": {
                    name: "Teste de Diabetes Gestacional",
                    frequency: "Entre 24-28 semanas de gravidez",
                    explanation: "Testa diabetes que se desenvolve durante a gravidez.",
                    recommendedAge: "Durante a gravidez",
                    whyItMatters: "A detecção e manejo precoces reduzem complicações para a mãe e o bebê.",
                    eligibility: "Mulheres grávidas após 24 semanas"
                },
                "Hepatitis B Screening": {
                    name: "Teste de Hepatite B",
                    frequency: "Na primeira consulta pré-natal",
                    explanation: "Testa infecção por hepatite B, que pode ser transmitida ao bebê.",
                    recommendedAge: "Durante a gravidez",
                    whyItMatters: "A detecção precoce permite intervenções para prevenir a transmissão ao bebê.",
                    eligibility: "Todas as mulheres grávidas"
                },
                "Intimate Partner Violence Screening": {
                    name: "Triagem de Violência por Parceiro Íntimo",
                    frequency: "Em consultas regulares",
                    explanation: "Avalia violência doméstica e fornece recursos de apoio.",
                    recommendedAge: "18-50 anos",
                    whyItMatters: "Identifica pessoas em risco e as conecta com serviços de apoio.",
                    eligibility: "Mulheres em idade reprodutiva"
                }
            }
        };

        // Event listeners
        document.addEventListener('DOMContentLoaded', function() {
            const checkButton = document.getElementById('checkButton');
            const genderSelect = document.getElementById('gender');
            const pregnantQuestion = document.getElementById('pregnantQuestion');
            
            checkButton.addEventListener('click', checkScreenings);
            
            // Show pregnancy question only for females
            genderSelect.addEventListener('change', function() {
                if (this.value === 'female') {
                    pregnantQuestion.classList.remove('hidden');
                } else {
                    pregnantQuestion.classList.add('hidden');
                    // Reset pregnancy radio buttons
                    document.querySelectorAll('input[name="pregnant"]').forEach(radio => {
                        if (radio.value === 'no') radio.checked = true;
                        else radio.checked = false;
                    });
                }
            });
            
            // Language selector
            const languageFlags = document.querySelectorAll('.language-flag');
            languageFlags.forEach(flag => {
                flag.addEventListener('click', function() {
                    const lang = this.getAttribute('data-lang');
                    setLanguage(lang);
                    
                    // Update active state
                    languageFlags.forEach(f => f.classList.remove('active'));
                    this.classList.add('active');
                });
            });

            // Limit height inputs
            document.getElementById('heightFeet').addEventListener('input', function() {
                if (this.value > 8) this.value = 8;
                if (this.value < 3) this.value = 3;
            });
            
            document.getElementById('heightInches').addEventListener('input', function() {
                if (this.value > 11) this.value = 11;
                if (this.value < 0) this.value = 0;
            });
            
            // Limit weight input
            const weightInput = document.getElementById('weight');

// Let the user type freely, but fix the value when they leave the field
weightInput.addEventListener('blur', function () {
    let value = parseInt(this.value, 10);
    if (!isNaN(value)) {
        if (value < 50) this.value = 50;
        else if (value > 500) this.value = 500;
    }
});

        });

        // Set language function
        function setLanguage(lang) {
            const elements = translations[lang];
            if (!elements) return;
            
            // Update all text elements
            for (const [id, text] of Object.entries(elements)) {
                const element = document.getElementById(id);
                if (element) element.textContent = text;
            }
            
            // Store current language
            window.currentLanguage = lang;
        }

        // Calculate BMI
        function calculateBMI(heightFeet, heightInches, weightLbs) {
            // Convert height to inches
            const heightInchesTotal = (heightFeet * 12) + heightInches;
            
            // BMI formula: (weight in pounds × 703) ÷ (height in inches)²
            const bmi = (weightLbs * 703) / (heightInchesTotal * heightInchesTotal);
            
            return parseFloat(bmi.toFixed(1));
        }

        // Get BMI category
        function getBMICategory(bmi, lang = 'en') {
            const categories = {
                en: {
                    underweight: "Underweight",
                    normal: "Normal weight",
                    overweight: "Overweight",
                    obese: "Obese"
                },
                es: {
                    underweight: "Bajo peso",
                    normal: "Peso normal",
                    overweight: "Sobrepeso",
                    obese: "Obesidad"
                },
               pt: {
    underweight: "Abaixo do peso",
    normal: "Peso normal",
    overweight: "Sobrepeso",
    obese: "Obesidade"
  }
};

if (bmi < 18.5) return categories[lang].underweight;
if (bmi < 25) return categories[lang].normal;
if (bmi < 30) return categories[lang].overweight;
return categories[lang].obese;
}

function checkScreenings() {
    // Get current language or default to English
    const lang = window.currentLanguage || "en";

    // Get user inputs
    const age = parseInt(document.getElementById('age').value, 10);
    const sex = document.getElementById('gender').value;
    const heightFeet = parseInt(document.getElementById('heightFeet').value, 10);
    const heightInches = parseInt(document.getElementById('heightInches').value, 10);
    const weight = parseInt(document.getElementById('weight').value, 10);
    const pregnant = sex === "female" ? document.querySelector('input[name="pregnant"]:checked').value === "yes" : false;
    const tobaccoUser = document.querySelector('input[name="tobacco"]:checked').value === "yes";
    const sexuallyActive = document.querySelector('input[name="sexuallyActive"]:checked').value === "yes";
    const alcoholUser = document.querySelector('input[name="alcohol"]:checked')?.value === "yes";



    // Validation
    if (isNaN(age) || !sex || isNaN(heightFeet) || isNaN(heightInches) || isNaN(weight)) {
        alert(lang === "es" ? "Por favor complete todos los campos requeridos." : (lang === "pt" ? "Por favor, preencha todos os campos obrigatórios." : "Please fill out all required fields."));
        return;
    }

    // Calculate BMI
    const bmi = calculateBMI(heightFeet, heightInches, weight);
    const bmiCategory = getBMICategory(bmi, lang);

    // Show BMI in results
    document.getElementById('bmiValue').textContent = bmi;
    document.getElementById('bmiCategory').textContent = bmiCategory;
    document.getElementById('bmiResult').classList.remove('hidden');
    document.getElementById('bmiLabel').textContent = translations[lang].bmiLabel;

    // Build screening list
    let allScreenings = [...screenings.general];
    if (sex === "female") allScreenings = allScreenings.concat(screenings.female);
    if (sex === "male") allScreenings = allScreenings.concat(screenings.male);

    // Filter screenings
const userScreenings = allScreenings.filter(s => {
    if (typeof s.minAge === "number" && age < s.minAge) return false;
    if (typeof s.maxAge === "number" && age > s.maxAge) return false;
    if (s.sex && s.sex !== "all" && s.sex !== sex) return false;
    if (s.bmiRequired && bmi < s.bmiRequired) return false;
    if (s.requirePregnant && !pregnant) return false;
    if (s.requireTobacco && !tobaccoUser) return false;
    if (s.requireSexuallyActive && !sexuallyActive) return false;
    if (s.name === "Unhealthy Alcohol Use Screening" && !alcoholUser) return false;

    return true;
});

 // ✅ Sort: A first, then B
    userScreenings.sort((a, b) => {
        if (a.grade === b.grade) return 0;
        return a.grade === "A" ? -1 : 1;
    });
    // Translate results if needed
    const resultListHtml = userScreenings.map(screen => {
        let label = screen.name;
        let frequency = screen.frequency;
        let explanation = screen.explanation;
        let recommendedAge = screen.recommendedAge;
        let whyItMatters = screen.whyItMatters;
        let eligibility = screen.eligibility;
        let talkWithDoctor = screen.talkWithDoctor;
        let icon = screen.icon;
        // Translate
        if (lang !== "en" && screeningTranslations[lang][screen.name]) {
            const t = screeningTranslations[lang][screen.name];
            label = t.name || label;
            frequency = t.frequency || frequency;
            explanation = t.explanation || explanation;
            recommendedAge = t.recommendedAge || recommendedAge;
            whyItMatters = t.whyItMatters || whyItMatters;
            eligibility = t.eligibility || eligibility;
            if (t.talkWithDoctor) talkWithDoctor = t.talkWithDoctor;
        }
        // Grade badge
        const gradeClass = screen.grade === "A" ? "grade-a" : "grade-b";
        return `
            <div class="relative bg-blue-50 border border-blue-200 rounded-lg p-4 mb-4 shadow-sm">
    <div class="flex justify-between items-start mb-2">
      <div class="flex items-center space-x-2">
        <span class="text-xl">${icon}</span>
        <span class="text-lg font-bold text-blue-900">${label}</span>
      </div>
      <div class="grade-badge ${gradeClass}">${screen.grade}</div>
    </div>

    <div class="text-sm text-gray-700 mb-2 flex flex-col md:flex-row md:flex-wrap gap-y-1 gap-x-6">
      <div><span class="font-semibold">Frequency:</span> ${frequency}</div>
      <div><span class="font-semibold">Recommended age:</span> ${recommendedAge}</div>
      <div><span class="font-semibold">Who needs it:</span> ${eligibility}</div>
    </div>

    <div class="text-gray-800 mb-2">${explanation}</div>

    <div class="text-blue-700 font-semibold">
  ✔ ${lang === "es" ? "Por qué es importante:" : lang === "pt" ? "Por que é importante:" : "Why it matters:"}
  ${whyItMatters}
</div>


    ${talkWithDoctor ? `
      <div class="talk-with-doctor mt-2 text-gray-600">
        ${lang === "es" ? "Hable con su médico" : (lang === "pt" ? "Converse com seu médico" : "Talk to your doctor about your personal and family history to see if this test is appropriate for you.")}
        ${typeof talkWithDoctor === "string" ? ": " + talkWithDoctor : ""}
      </div>` : ""}
  </div>
`;
    }).join("");

    // Show results
    document.getElementById('screeningResults').innerHTML = resultListHtml;
    document.getElementById('resultsSection').classList.remove('hidden');

    // Print-only section
    document.getElementById('printAge').textContent = age;
    document.getElementById('printSex').textContent = (sex === "male" ? translations[lang].maleOption : translations[lang].femaleOption);
    document.getElementById('printBMI').textContent = bmi + " (" + bmiCategory + ")";
    document.getElementById('printDate').textContent = new Date().toLocaleDateString();

    // Scroll to results
    document.getElementById('resultsSection').scrollIntoView({behavior: "smooth"});
}

</script>
</body>
</html>
