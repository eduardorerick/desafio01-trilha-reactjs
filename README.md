<h1 align="center"> Ignite </h1>
<h2 align="center">Desafio 01 da Trilha ReactJS </h2>


![image](https://user-images.githubusercontent.com/82004348/126047335-70a05e1c-882b-4a72-8c61-23de06041941.png)

<h3>Resultado dos testes </h3>

![image](https://user-images.githubusercontent.com/82004348/126047241-6614f587-9211-4391-9e48-cebe994f9e24.png)



<h3> Explicando o desafio </h3>

No desafio, foi pedido que eu alterasse o componente <code> TaskList.tsx </code> para que acressentasse as seguintes funcionalidades : 

<ul> 
<li>handleCreateNewTask</li>
<li>handleToggleTaskCompletion</li>
<li>handleRemoveTask</li>
<ul/> 

<h3>Minha resolução</h3>

<h4>handleCreateNewTask</h4>

<p> O primeiro passo que eu dei para criar um novo task foi fazer uma variável para gerar um número aleatório para ser o id da task. </p>

    let random = Math.random() * 100000;

<p> Sabendo o tipo do meu estado ficou fácil de acrescentar novos dados nele. </p> 

    interface Task {
      id: number;
      title: string;
      isComplete: boolean;
    }
    
    
    const [tasks, setTasks] = useState<Task[]>([]);
    
    
<p> Então para acrescentar o novo task basta adicionar um objeto com os dados que eu quero nesse array, além de adicionar as tasks anteriores com o spread operator. </p>


    setTasks([...tasks, {id: random, title: newTaskTitle, isComplete: false}]
    
<p> E para cumprir com os requisitos de teste coloco um condicional if() <code> if (newTaskTitle.trim() !== "" ) </code> ficando da seguinte forma: 

    function handleCreateNewTask() {
        if (newTaskTitle.trim() !== "" ) {
        let random = Math.random() * 100000;
        setTasks([...tasks, {id: random, title: newTaskTitle, isComplete: false}] )
        }
      }
      
<h4> handleToggleTaskCompletion(id) </h4>

<p> Para mudar uma propriedade de um objeto dentro de um array, utilizeio metodo <code>.map()</code>, para eu conseguir checar cada objeto dentro do array (cada task na lista) e ver se bate com o id que foi passado na função.</p>

    const updatedTasks = tasks.map( task => {
          if(task.id === id) {
            return {...task, isComplete:!task.isComplete }
          }
          return task
        })
        setTasks(updatedTasks)
    }
        
<p>O que o código acima faz é: Se o task atual tem o mesmo id, o spread operator (...) vai passar todo o objeto task e todas as suas propriedades e então ele atualiza apenas as props que passamos para ele. Caso não seja o meso id, ele retorna o task da mesma maneira. e então atualizo os tasks com o updatedTasks</p>


<h4> function handleRemoveTask(id) </h4>

<p> Esse, para mim, foi o mais simples dos 3, para remover basta usarmos o <code>.filter()</code>, passamos para ele uma condicional, e ele vai retornar apenas os elementos para quais retornaram true.

Então: 

      function handleRemoveTask(id: number) {
          setTasks(
            tasks.filter(task => task.id !== id)
          )
      }
      

<h1> Fim do desafio e até o próximo nível! </h1>

