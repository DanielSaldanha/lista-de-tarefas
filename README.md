# lista-de-tarefas
using System;
using System.Collections.Generic;
using System.Collections.Specialized;
using System.ComponentModel;
using System.ComponentModel.Design.Serialization;
using System.Linq;
using System.Runtime.InteropServices;
using System.Security.Cryptography;
using System.Text;
using System.Threading.Tasks;

namespace praticando
{
    internal class Program
    {
        static int index = 0, IndiceTarefa = 0;
        static string[] tarefas = new string[10];
        static void Main(string[] args)
        {
            bool controlador = true;
           
            string comandos = "0";

           
            while (controlador == true)
            {   
               if(comandos == "0")
                {
                    Console.Clear();
                    Console.Write("digite um comando entre 1, 2, 3 e 4 a seguir: ");
                    comandos = Console.ReadLine();

                }
               else if(comandos == "1")
               {
                   
                    ExibirTarefas();
                    Console.ReadLine();
                    comandos = "0";
                }
               else if (comandos == "2")
                {
                    AddTarefa();
                    comandos = "0";
                }
               else if(comandos == "3")
                {
                   
                    removerTarefa();
                    Console.ReadLine();
                    comandos = "0";
                }
               else if(comandos == "4")
                {

                    TarefaConcluida();
                    Console.ReadLine();
                    comandos = "0";
                }
                else
                {

                    Console.WriteLine("nao foi possivel executar este comando");
                    controlador = false;
                }            
            }
            Console.ReadLine();
        }
        static void AddTarefa()
        {
            Console.WriteLine("digite uma tarefa");
            string trf = Console.ReadLine();
            tarefas[index] += trf;
            index++;

        }
       static void removerTarefa()
        {
            Console.WriteLine("tarfea a ser apagada");

            for (int i = 0; i < index; i++)
            {
                Console.Write(i + ", ");
            }
            int posicaoTarefa = 0;
            Console.WriteLine("selecione uma das alternativas");
            posicaoTarefa = int.Parse(Console.ReadLine());

            int aux = index;
            index = posicaoTarefa;
            tarefas[index] = "(apagada)";
            index = aux;


                  
            if(index <= 0)
            {
                index = 0;
            }

        }
      static void TarefaConcluida()
      {
            Console.WriteLine("selecione uma atrefa a ser concluida");
            for (int i = 0; i < index; i++)
            {
                Console.Write(i + ", ");
            }
            int posicaoTarefa = 0;
            Console.WriteLine("selecione uma das alternativas");
            posicaoTarefa = int.Parse(Console.ReadLine());

            int aux = index;
            index = posicaoTarefa;
            tarefas[index] += " (Concluida) ";
            index = aux;


        }
        static void ExibirTarefas()
        {
            Console.WriteLine("tarefa exibida");
            foreach (string valor in tarefas)
            {
                Console.WriteLine(valor);
            }
        }
    }
}
