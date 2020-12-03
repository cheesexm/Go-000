func dao() error {
	var name string
	err := db.QueryRow("select name from users where id = ?", 1).Scan(&name)
	return errors.Wrap(err, "sql.ErrNoRows")
}

func service() error {
	err := dao()
	if err != nil {
		return err
	}
}
func conntraller() error {
	err := service()
	if err != nil {
		fmt.Printf("error:%+v", err)
	}
}