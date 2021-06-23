using System;
using System.Collections.Generic;
using System.Linq;

namespace _04hhhh
{
    class Program
    {
        static void Main(string[] args)
        {
            List<int> inList = Console.ReadLine()
                .Split()
                .Select(int.Parse)
                .ToList();
            string command = Console.ReadLine();

            while (command != "End")
            {
                List<string> inTo = command.Split().ToList();

                if (inTo[0] == "Add")
                {
                    inList.Add(int.Parse(inTo[1]));
                }
                else if (inTo[0] == "Remove")
                {
                    if (int.Parse(inTo[1]) >= inList.Count || int.Parse(inTo[1]) < 0)
                    {
                        Console.WriteLine("Invalid index");
                    }
                    else
                    {
                        inList.RemoveAt(int.Parse(inTo[1]));
                    }

                }
                else if (inTo[0] == "Insert")
                {
                    if (int.Parse(inTo[2]) >= inList.Count || int.Parse(inTo[2]) < 0)
                    {
                        Console.WriteLine("Invalid index");
                    }
                    else
                    {
                        inList.Insert(int.Parse(inTo[2]), int.Parse(inTo[1]));
                    }

                }
                else if (inTo[0] == "Shift")
                {
                    if (inTo[1] == "left")
                    {
                        for (int i = 0; i < int.Parse(inTo[2]); i++)
                        {
                            int firstPosition = inList[0];
                            inList.RemoveAt(0);
                            inList.Add(firstPosition);


                        }
                    }
                    else if (inTo[1] == "right")
                    {
                        for (int i = 0; i < int.Parse(inTo[2]); i++)
                        {
                            int lastPosition =inList[inList.Count- 1];
                            inList.RemoveAt(inList.Count - 1);
                            inList.Insert(0, lastPosition);
                        }

                    }
                }

                command = Console.ReadLine();
            }
            Console.WriteLine(string.Join(" ", inList));
        }
    }
}

