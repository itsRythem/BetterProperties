# BetterProperties
EXAMPLE

	protected static String directoryPath = ".";
	protected static File directory = new File(directoryPath);
	protected static File configFile = new File(addFile("config.yml", directory));
	protected static Properties config;
  
  	protected static void loadProperties() {
		if(!configFile.exists()) {
			try {
				configFile.createNewFile();		
				
				OutputStream output = new FileOutputStream(configFile);
				Properties prop = new Properties();
				
				prop.setProperty("test", "value");

				prop.store(output);
			}catch(Exception e) {
				System.out.println("Error creating config");
				e.printStackTrace();
			}
		}
		
		if(configFile.exists()) {
			config = null;
			
			try {
				InputStream input = new FileInputStream(configFile);
				config = new Properties();
				config.load(input);
			}catch(Exception e) {
				System.out.println("Error loading config");
				e.printStackTrace();
			}

		}
	}
