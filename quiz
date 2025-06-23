import React from 'react';

const Component = () => {
  const [currentQuestion, setCurrentQuestion] = React.useState(0);
  const [showScore, setShowScore] = React.useState(false);
  const [score, setScore] = React.useState(0);
  const [selectedAnswer, setSelectedAnswer] = React.useState(null);
  const [isAnswered, setIsAnswered] = React.useState(false);

  const questions = [
    {
      questionText: 'What does AI stand for?',
      answerOptions: [
        { answerText: 'Automated Intelligence', isCorrect: false },
        { answerText: 'Artificial Intelligence', isCorrect: true },
        { answerText: 'Augmented Innovation', isCorrect: false },
        { answerText: 'Advanced Integration', isCorrect: false },
      ],
    },
    {
      questionText: 'Which of these is NOT a type of machine learning?',
      answerOptions: [
        { answerText: 'Supervised Learning', isCorrect: false },
        { answerText: 'Unsupervised Learning', isCorrect: false },
        { answerText: 'Reinforcement Learning', isCorrect: false },
        { answerText: 'Cognitive Learning', isCorrect: true },
      ],
    },
    {
      questionText: 'Which AI technique is designed to mimic the way the human brain works?',
      answerOptions: [
        { answerText: 'Neural Networks', isCorrect: true },
        { answerText: 'Decision Trees', isCorrect: false },
        { answerText: 'Random Forests', isCorrect: false },
        { answerText: 'Support Vector Machines', isCorrect: false },
      ],
    },
    {
      questionText: 'What is the Turing Test used to determine?',
      answerOptions: [
        { answerText: 'Computer processing speed', isCorrect: false },
        { answerText: 'Machine\'s ability to exhibit human-like intelligence', isCorrect: true },
        { answerText: 'Algorithm efficiency', isCorrect: false },
        { answerText: 'Network security vulnerabilities', isCorrect: false },
      ],
    },
    {
      questionText: 'Which company developed the AI system that defeated the world champion in the game of Go?',
      answerOptions: [
        { answerText: 'Microsoft', isCorrect: false },
        { answerText: 'IBM', isCorrect: false },
        { answerText: 'Google (DeepMind)', isCorrect: true },
        { answerText: 'OpenAI', isCorrect: false },
      ],
    },
  ];

  const handleAnswerClick = (isCorrect, index) => {
    if (isAnswered) return;
    
    setSelectedAnswer(index);
    setIsAnswered(true);
    
    if (isCorrect) {
      setScore(score + 1);
    }
    
    setTimeout(() => {
      const nextQuestion = currentQuestion + 1;
      if (nextQuestion < questions.length) {
        setCurrentQuestion(nextQuestion);
        setSelectedAnswer(null);
        setIsAnswered(false);
      } else {
        setShowScore(true);
      }
    }, 1000);
  };

  const resetQuiz = () => {
    setCurrentQuestion(0);
    setShowScore(false);
    setScore(0);
    setSelectedAnswer(null);
    setIsAnswered(false);
  };

  const getButtonClass = (index) => {
    const baseClass = "w-full p-4 mb-2 rounded-lg text-left transition-colors duration-300 border";
    
    if (!isAnswered) {
      return `${baseClass} bg-white text-gray-800 border-gray-300 hover:bg-gray-100`;
    }
    
    if (questions[currentQuestion].answerOptions[index].isCorrect) {
      return `${baseClass} bg-green-500 text-white border-green-600`;
    }
    
    if (selectedAnswer === index && !questions[currentQuestion].answerOptions[index].isCorrect) {
      return `${baseClass} bg-red-500 text-white border-red-600`;
    }
    
    return `${baseClass} bg-white text-gray-400 border-gray-200`;
  };

  return (
    <div className="min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-500 to-purple-600 p-4">
      <div className="bg-white rounded-xl shadow-2xl p-6 md:p-8 w-full max-w-md">
        {showScore ? (
          <div className="text-center">
            <h2 className="text-3xl font-bold text-gray-800 mb-4">Quiz Complete!</h2>
            <div className="text-5xl font-bold mb-6 text-blue-600">{score} / {questions.length}</div>
            <p className="text-gray-600 mb-8">
              {score === questions.length 
                ? "Perfect score! You're an AI expert!" 
                : score >= questions.length / 2 
                  ? "Good job! You know your AI basics."
                  : "Keep learning about AI!"}
            </p>
            <button 
              onClick={resetQuiz}
              className="bg-blue-600 hover:bg-blue-700 text-white font-bold py-3 px-6 rounded-lg transition-colors duration-300"
            >
              Restart Quiz
            </button>
          </div>
        ) : (
          <>
            <div className="mb-6">
              <div className="flex justify-between items-center mb-4">
                <h2 className="text-xl font-bold text-gray-800">AI Quiz</h2>
                <div className="text-sm font-medium text-gray-500">
                  Question {currentQuestion + 1}/{questions.length}
                </div>
              </div>
              <div className="w-full bg-gray-200 rounded-full h-2.5">
                <div 
                  className="bg-blue-600 h-2.5 rounded-full transition-all duration-500" 
                  style={{ width: `${((currentQuestion + 1) / questions.length) * 100}%` }}
                ></div>
              </div>
            </div>
            
            <div className="mb-6">
              <h3 className="text-xl md:text-2xl font-bold text-gray-800 mb-4">
                {questions[currentQuestion].questionText}
              </h3>
              <div className="space-y-2">
                {questions[currentQuestion].answerOptions.map((answerOption, index) => (
                  <button
                    key={index}
                    onClick={() => handleAnswerClick(answerOption.isCorrect, index)}
                    className={getButtonClass(index)}
                    disabled={isAnswered}
                  >
                    <span className="flex items-center">
                      <span className="w-6 h-6 flex items-center justify-center rounded-full border border-gray-300 mr-3">
                        {String.fromCharCode(65 + index)}
                      </span>
                      {answerOption.answerText}
                    </span>
                  </button>
                ))}
              </div>
            </div>
          </>
        )}
      </div>
    </div>
  );
};

export default function App() {
  return (
    <Component />
  );
}
