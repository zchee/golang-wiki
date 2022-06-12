func main() {
	str, err := json.Marshal([]uint8{2})
	fmt.Println(string(str), err)
}

As the code above. It will print a "AG==" when i pass an array of type uint8.