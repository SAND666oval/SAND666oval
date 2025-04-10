import { useState } from "react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { motion } from "framer-motion";

const scenes = [
  {
    id: 1,
    title: "La Biblioteca Encantada",
    text: "Despiertas en una biblioteca antigua. Una nota descansa sobre una mesa: 'Hoy es un día especial. La historia que vivimos merece ser contada. Encuentra el libro que guarda la primera pista.'",
    options: ["La Playa de los Sueños", "El Viaje de Stitch", "Notas de un Corazón"],
    correct: "Notas de un Corazón"
  },
  {
    id: 2,
    title: "El Acantilado Musical",
    text: "El sonido de una melodía conocida te guía: 'Mine - The 1975'. En una roca, hay una grabación con tu frase: 'Sabes que siempre estaré a tus pies.'",
    options: ["Seguir la melodía", "Volver a la biblioteca"],
    correct: "Seguir la melodía"
  },
  {
    id: 3,
    title: "La Playa de los Recuerdos",
    text: "Botellas en la arena contienen imágenes de momentos vividos. Al abrir una, ves una foto tuya sonriendo con amor. El mar susurra: 'Estás cerca...'",
    options: ["Abrir el cofre"],
    correct: "Abrir el cofre"
  },
  {
    id: 4,
    title: "El Cofre del Tesoro",
    text: `Sé que quizá no soy el mejor haciendo este tipo de cosas, pero lo hago con muchísimo amor y con el mayor esfuerzo por hacerlo bien.\n\nComo sabrás… Hoy es 10 de abril, es un día sumamente especial y, créeme que sé, yo sé o creía saber que no es un día como tal de tu agrado. Para mí honestamente es todo lo contrario. ¿Qué te puedo decir? Para mí es tener la dicha (porque lo considero como un mayor regalo) el hecho de poder permanecer en tu vida y disfrutar este tipo festividades.\n\nEres la persona más resiliente, valiente, fuerte, maravillosa, hermosa, un ser humano tan divino y hermoso en todo sentido, admirable, tan emblemática y sublime. Dios, yo te admiro y te he admirado tanto, no sabes la alegría que siento por cada uno de tus logros, el orgullo que me invade cada vez que sientes que no puedes, pero entregas el doble sin importar qué tan quemada estás. Yo en serio te admiro. Creas o no, agradezco tanto, no sé a quién, pero agradezco tanto el hecho de que existas, de que me permitas existir en tu vida y me des la oportunidad diaria de conocerte, es una sensación de un amor tan genuino y puro que me atraviesa.\n\nTe deseo lo mejor, siempre pido lo mejor llegue a ti y siempre desearé lo mejor para ti, tu felicidad, esa vibra tan hermosa que tienes y que esa cabecita divina permanezca así. Te amo, te amo hoy, mañana y siempre.\n\nFeliz cumpleaños para ti, mi brujita.`,
    options: [],
    correct: null
  }
];

export default function EscapeRoom() {
  const [step, setStep] = useState(0);

  const handleOptionClick = (option: string) => {
    if (option === scenes[step].correct) {
      setStep((prev) => prev + 1);
    }
  };

  const currentScene = scenes[step];

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-100 to-purple-200 p-6 flex flex-col items-center justify-center text-center">
      <motion.div
        className="max-w-xl w-full"
        initial={{ opacity: 0, y: 20 }}
        animate={{ opacity: 1, y: 0 }}
        transition={{ duration: 0.6 }}
      >
        <Card className="rounded-2xl shadow-xl p-4">
          <CardContent>
            <h2 className="text-2xl font-semibold mb-4">{currentScene.title}</h2>
            <p className="mb-6 whitespace-pre-line">{currentScene.text}</p>
            <div className="flex flex-col gap-2">
              {currentScene.options.map((option, index) => (
                <Button
                  key={index}
                  onClick={() => handleOptionClick(option)}
                  className="bg-purple-500 hover:bg-purple-600 text-white"
                >
                  {option}
                </Button>
              ))}
            </div>
          </CardContent>
        </Card>
      </motion.div>
    </div>
  );
}
