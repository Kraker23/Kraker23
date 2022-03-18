## Quien Soy?
 ```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

using System.Text.Json;
namespace MiVida
{
    public static class Program
    {
        public static void Main()
        {
            Yo me = new Yo();

            string jsonString = JsonSerializer.Serialize(me);
        }
    }

    public class Yo
    {
        public string nombre { get { return "Cristian Javier"; } }
        public string apellidos { get { return "Ramirez Arroyo"; } }
        public string poblacion { get { return "Barcelona"; } }

        public List<Estudio> estudios { get; set; }
        public List<Trabajo> trabajos { get; set; }
        public List<Herramientas> herramientas { get; set; }

        public Yo()
        {
            Estudiar();
            Trabajar();
            Herramientas();
        }



        private void Estudiar()
        {
            estudios = new List<Estudio>();
            estudios.Add(
                   new Estudio
                   {
                       formacion = "Bachillerato Tecnologio",
                       Lugar = "IES Salvador Espriu",
                       poblacion = "Barcelona",
                       fechaInicio = new DateTime(2010, 9, 1),
                       fechaFinal = new DateTime(2013, 6, 25),
                       explicacion = ""
                   }
                   );
            estudios.Add(
                new Estudio
                {
                    formacion = "CFGS AUTOMAITZACION Y ROBOTICA INDUSTRIAL",
                    Lugar = "INS AGUSTI SERRA I FONTANET ",
                    poblacion = "Sabadell",
                    fechaInicio = new DateTime(2013, 9, 1),
                    fechaFinal = new DateTime(2015, 6, 25),
                    explicacion = "Aprendizaje, manipulación y programación sobre autómatas y robots industriales,y su programación." +
                                "Mayormente utilizado el lenguaje C y C++. Y creación de proyectos de domotica en arduino.",
                    extra = "Practicas -> En la Universidad Politécnica de Terrassa, diseñando y programando pantallas HMI, para una empresa de Sevilla (SEPTIEMBRE 2014 – ABRIL 2015)."
                }
                );

            estudios.Add(
               new Estudio
               {
                   formacion = "CFGS DESARROLLO DE APLICACIONES MULTIPLATAFORMA",
                   Lugar = " INS POBLENOU ",
                   poblacion = "Barcelona",
                   fechaInicio = new DateTime(2015, 9, 1),
                   fechaFinal = new DateTime(2017, 6, 25),
                   explicacion = "Enseñanza sobre programación en Java, instalación de sistemas operativos, diseño de paginas webs." +
                                 "Practicas de formación Dual(Eskape Consulting SL).",
                   extra = "Proyecto final sobre IoT , siendo finalistas de la 3ª edición del Innolab (Citilab - Baix Llobregat) a proyecto más innovador" +
                                "Y ganadores del concurso BIZZ DE BARCELONA sobre proyecto más innovador."
               }
               );
        }
        private void Trabajar()
        {

            trabajos = new List<Trabajo>();
            trabajos.Add(
                   new Trabajo
                   {
                       puesto = "Camarero",
                       empresa = "Restaurante familiar",
                       fechaInicio = new DateTime(2009, 6, 1),
                       fechaFinal = new DateTime(2013, 6, 25),
                       trabajosRealizado = "Atender a los clientes, preparar pedidos, revisar inventario, comprar inventario..."
                   }
                   );
            trabajos.Add(
                   new Trabajo
                   {
                       puesto = "Cerrajero ayudante",
                       empresa = "Empresa de Cerrajeria",
                       fechaInicio = new DateTime(2015, 6, 1),
                       fechaFinal = new DateTime(2016, 6, 1),
                       trabajosRealizado = "Ayuda a un familiar en el tema de gestionar citas con los clientes para poder efectuar las incidencias. " +
                                        "Revisar material, preparar rutas de trabajo. Gestionar facturacion."

                   }
                   );

            trabajos.Add(
                   new Trabajo
                   {
                       puesto = "Programador",
                       empresa = "ESKAPE CONSULTING S.L.",
                       fechaInicio = new DateTime(2016, 6, 1),
                       fechaFinal = DateTime.Now,
                       trabajosRealizado = " - Creación y mantenimiento de páginas internas de la empresa para el servicio Itil, con tecnología MVC. " +
                       " - Desarrollo de la parte de Reporting de un programa para las ITVs" +
                        "Mantenimiento y desarrollo de un programa dedicado a los anuncioas (Television y Internet). De mas de 15 años de desarrollo. Mantenimiento de su respectiva base de datos. " +
                        "Con uso diario, con mas de 300 usuarios activos al día." +
                        "Y resolución de incidencias." +
                        " - Desarrollo y gestion de un proyecto para las ITVs (destinado a fuera de España). Para adaptar un programa existenta a una version con las necesidades del cliente nuevo." +
                        "Realizar comunicacion con el cliente para evaluar requerimientos y necesidades, para adpatarlas al programa actual."
                   }
                   );
        }
        private void Herramientas()
        {
            herramientas = new List<Herramientas>();
            herramientas.Add(new Herramientas("Lenguajes Progrmaacion", "C#", "Java", "VisualBasic", "C", "C++", "Pyhton"));
            herramientas.Add(new Herramientas("IDEs", "Visual Studio", "IntellIJ Idea", "Android Studio"));
            herramientas.Add(new Herramientas("Base Datos", "TSQL", "MySql", "FireBase"));
            herramientas.Add(new Herramientas("Web", "HTML", "CSS", "JavaScript", "Postman", "bootstrap", "node.js", "Angular", "PHP"));
            herramientas.Add(new Herramientas("Editores", "Sublime Text", "NotePad ++", ""));
            herramientas.Add(new Herramientas("Otras Herramientas", "Forks", "git", ""));
            herramientas.Add(new Herramientas("Otros ", "Arduino", "Raspberry Pi", "Unity"));
        }       
    }

    public class Estudio
    {
        public string formacion { get; set; }
        public string Lugar { get; set; }
        public string poblacion { get; set; }
        public DateTime fechaInicio { get; set; }
        public DateTime fechaFinal { get; set; }
        public string explicacion { get; set; }
        public string extra { get; set; }
    }

    public class Trabajo
    {
        public string puesto { get; set; }
        public string empresa { get; set; }
        public string trabajosRealizado { get; set; }
        public DateTime? fechaInicio { get; set; }
        public DateTime? fechaFinal { get; set; }
    }
    public class Herramientas
    {
        public Herramientas(string categoria, params string[] nombres)
        {
            this.categoria = categoria;
            this.nombres = nombres.ToList();
        }
        public string categoria { get; set; }
        public List<string> nombres { get; set; }
    }
}

 ```






