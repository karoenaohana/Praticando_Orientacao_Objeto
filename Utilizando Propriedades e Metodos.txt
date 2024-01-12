using System;
class Robo
{
    public int VelocidadeAtual { get; set; } = 0;
    public int VelocidadeMaxima { get;}
    public int VelocidadeMinima { get;}
    public int VelocidadeFinal {get; set;}
    
    public Robo(int vmin, int vmax)
    {
        VelocidadeMinima = vmin;
        VelocidadeMaxima = vmax;
        VelocidadeAtual = vmin;
        VelocidadeFinal = VelocidadeAtual;
    }
    public void Acelerar()
    {
        if (VelocidadeAtual < VelocidadeMaxima)
        {
            VelocidadeAtual++;
        }
    }
    public void Desacelerar()
    {
        if (VelocidadeAtual > VelocidadeMinima)
        {
            VelocidadeAtual--;
        }
    }   
    public void Calcular(string Comandos)
    {
      foreach(char c in Comandos)
      {
        if(c == 'A')
        {
          Acelerar();
        }
        
        else if(c == 'D')
        {
          Desacelerar();
        }
      }
    }
}
class Program
{
    static void Main()
    {
      string Values = Console.ReadLine();
      string[] Numbers = Values.Split(' ');
      int Vmin = int.Parse(Numbers[0]);
      int Vmax = int.Parse(Numbers[1]);
     
      string comandos = Console.ReadLine().ToUpper();
      Robo robo = new Robo(Vmin, Vmax);
      robo.Calcular(comandos);
      Console.WriteLine(robo.VelocidadeAtual);
    }
}