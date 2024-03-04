import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.edge.EdgeDriver;
import org.openqa.selenium.interactions.Actions;
import org.testng.annotations.Test;

public class Test1 {
	WebDriver driver;

	@Test
	public void LamdaTest1() throws InterruptedException {
		System.setProperty("webdriver.chrome.driver",
				"C:\\Users\\1000506\\eclipse-workspace\\Lamda.test\\Driver\\chromedriver.exe");
		driver = new ChromeDriver();
		driver.manage().window().maximize();
		Thread.sleep(5000);
		driver.get("https://www.lambdatest.com/selenium-playground");
		driver.findElement(By.linkText("Simple Form Demo")).click();
		String currentUrl = driver.getCurrentUrl();
		if (currentUrl.contains("simple-form-demo")) {
			System.out.println("URL validation passed.");
		} else {
			System.out.println("URL validation failed.");
		}
		String welcomeMessage = "Welcome to LambdaTest";
		WebElement messageInput = driver.findElement(By.cssSelector("input#user-message")); // *[@id="showInput"]
		messageInput.sendKeys(welcomeMessage);
		driver.findElement(By.xpath("//*[@id='showInput']")).click();
		WebElement outputMessage = driver.findElement(By.xpath("//*[@id='message']"));
		String displayedMessage = outputMessage.getText();
		if (displayedMessage.equals(welcomeMessage)) {
			System.out.println("Message validation passed.");
		} else {
			System.out.println("Message validation failed.");
		}
		Thread.sleep(2000);
		driver.close();
	}

	@Test
	public void LamdaTest2() throws InterruptedException {
		System.setProperty("webdriver.edge.driver",
				"C:\\Users\\1000506\\eclipse-workspace\\Lamda.test\\Driver\\msedgedriver.exe");
		driver = new EdgeDriver();
		driver.manage().window().maximize();
		Thread.sleep(5000);
		driver.get("https://www.lambdatest.com/selenium-playground");
		driver.findElement(By.linkText("Drag & Drop Sliders")).click();
		WebElement slider = driver.findElement(By.cssSelector("input[value='15']"));
		Actions action = new Actions(driver);
		action.clickAndHold(slider).moveByOffset(212, 0).release().perform();
		WebElement rangeValue = driver.findElement(By.xpath("//*[@id='rangeSuccess']"));
		String actualValue = rangeValue.getText();
		String expectedValue = "95";
		if (actualValue.equals(expectedValue)) {
			System.out.println("Slider validation passed.");
		} else {
			System.out.println("Slider validation failed. Actual value: " + actualValue);
		}
		Thread.sleep(2000);
		driver.close();
	}

	
	  @Test public void LamdaTest3() throws InterruptedException {
	  System.setProperty("webdriver.chrome.driver",
	  "C:\\Users\\1000506\\eclipse-workspace\\Lamda.test\\Driver\\chromedriver.exe"
	  ); driver = new ChromeDriver(); driver.manage().window().maximize();
	  driver.get("https://www.lambdatest.com/selenium-playground");
	  Thread.sleep(1000);
	  driver.findElement(By.linkText("Input Form Submit")).click();
	  driver.findElement(By.xpath("//*[@id='seleniumform']/div[6]/button")).click()
	  ;
	  
	  // Assert "Please fill in the fields" error message
	  
	  
		/*
		 * WebElement errorMessage =
		 * driver.findElement(By.cssSelector("small[class='error-message']")); String
		 * actualErrorMessage = errorMessage.getText(); String expectedErrorMessage =
		 * "Please fill in the fields."; if
		 * (actualErrorMessage.equals(expectedErrorMessage)) {
		 * System.out.println("Error message validation passed."); } else {
		 * System.out.println("Error message validation failed. Actual message: " +
		 * actualErrorMessage); }
		 */
	  
	  
	  
	  driver.findElement(By.name("name")).sendKeys("John Doe");
	  driver.findElement(By.xpath("//*[@id='inputEmail4']")).sendKeys(
	  "john@gmail.com");
	  driver.findElement(By.name("password")).sendKeys("Lamda@123");
	  driver.findElement(By.name("company")).sendKeys("BMW");
	  driver.findElement(By.name("website")).sendKeys("BMW@yopmail.com");
	  
	  WebElement countryDropdown = driver.findElement(By.name("country"));
	  countryDropdown.sendKeys("United States");
	  driver.findElement(By.name("city")).sendKeys("BANGALORE");
	  driver.findElement(By.name("address_line1")).sendKeys("#109 ABC street");
	  driver.findElement(By.name("address_line2")).sendKeys("Commercial line");
	  driver.findElement(By.id("inputState")).sendKeys("KARNATAKA");
	  driver.findElement(By.name("zip")).sendKeys("560065");
	  
	  driver.findElement(By.xpath("//*[@id='seleniumform']/div[6]/button")).click()
	  ;
	  
	  WebElement successMessage = driver.findElement(By.xpath(
	  "//*[@id='__next']/div/section[2]/div/div/div/div/p")); String
	  actualSuccessMessage = successMessage.getText(); String
	  expectedSuccessMessage =
	  "Thanks for contacting us, we will get back to you shortly."; if
	  (actualSuccessMessage.equals(expectedSuccessMessage)) {
	  System.out.println("Success message validation passed."); } else {
	  System.out.println("Success message validation failed. Actual message: " +
	  actualSuccessMessage); }
	  
	  driver.close(); }
	 
}
