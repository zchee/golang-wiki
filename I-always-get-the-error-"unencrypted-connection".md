my go versioin:1.10
my code:
func main() {
	m := gomail.NewMessage()
	m.SetHeader("From", "XX@XX.com")
	m.SetHeader("To", "XX@XX.com")
	m.SetAddressHeader("Cc", "XX@XX.com", "Dan")
	m.SetHeader("Subject", "Hello!")
	m.SetBody("text/html", "Hello <b>Bob</b> and <i>Cora</i>!")
	m.Attach("/Users/XX/Workspaces/Goland/New_Test_Pro/file1.txt")

	d := gomail.NewDialer("smtp.XX.com", 80, "XX@XX.com", "XXX")
	d.TLSConfig = &tls.Config{InsecureSkipVerify: true}
	if err := d.DialAndSend(m); err != nil {
		fmt.Println(err)
		panic(err)
	}
}

thanks