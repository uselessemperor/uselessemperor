public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureAppConfiguration((hostingContext, config) =>
        {
            Console.WriteLine($"{DateTime.Now:yyyy-MM-dd HH:mm:ss:fff} - ConfigureAppConfiguration START");

            // Force config to build so you can see what providers are there:
            var builtConfig = config.Build();

            foreach (var source in config.Sources)
            {
                Console.WriteLine($"{DateTime.Now:yyyy-MM-dd HH:mm:ss:fff} - Config source: {source.GetType().Name}");
            }

            Console.WriteLine($"{DateTime.Now:yyyy-MM-dd HH:mm:ss:fff} - ConfigureAppConfiguration END");
        })
        .ConfigureLogging(logging =>
        {
            Console.WriteLine($"{DateTime.Now:yyyy-MM-dd HH:mm:ss:fff} - ConfigureLogging START");
        })
        .ConfigureWebHostDefaults(webBuilder =>
        {
            Console.WriteLine($"{DateTime.Now:yyyy-MM-dd HH:mm:ss:fff} - CreateHostBuilder -start ");
            webBuilder.UseStartup<Startup>();
            Console.WriteLine($"{DateTime.Now:yyyy-MM-dd HH:mm:ss:fff} - CreateHostBuilder -end ");
        });