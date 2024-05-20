# BirthdatNoteTaker
swift ile geliştirilmiştir.
birthdaynotetakerapp için adım adım aşağıdaki adımları yapalım.

 1- text field oluştur name ve birthday adlı iki tane oluştur.

2-button oluştur içine save (kaydetme butonu)yaz ve delete(sil) buton oluştur.

3-label oluştur name ve birthday yazılı iki tane oluştur.


 Cod oluşturun

1- textfield control tuşuyla basılı tutup sınıfın altına bırak nameTextField yaz aynısını birthdayTextField içinde yapıyoruz.

2-label control tuşuna basılı tutup text field altına bırakalım nameLabel yazalım aynısını birthdayLabel içinde yapalım.

3-button control tuşuna basılı tutup en aşağıya bırakalım çünkü actionumuz olacak saveClicked yazalım.

4- sınırları düzgün olması için reset to suggested constraints tuşuna basalım.










//
//  ViewController.swift
//  BirthdayNoteTaker
//

import UIKit

class ViewController: UIViewController {
    @IBOutlet weak var nameTextField: UITextField!
    @IBOutlet weak var birthdayTextField: UITextField!
    @IBOutlet weak var nameLabel: UILabel!
    @IBOutlet weak var birthdayLabel: UILabel!
    

    override func viewDidLoad() {
        super.viewDidLoad()
        
        let storedName = UserDefaults.standard.object(forKey: "name")
        let storedBirthday = UserDefaults.standard.object(forKey: "birthday")
        
        //Casting- as? vs. as!
        // as? yapabilirsenbu şekile casting et
        // as! yabirsen kesin çevirebilirsin
        if let newName = storedName as? String {
            nameLabel.text = "Name: \(newName)"
            // soredName string olarak kaydedebirisen(if let ) my name diye
            // bir şey oluştur.
        }
        if let newBirthday = storedBirthday as? String {
            birthdayLabel.text = "Birthday : \(newBirthday)"
        }
        
    }
    @IBAction func saveClicked(_ sender: Any) {
        UserDefaults.standard.set(nameTextField.text!, forKey: "name")
        UserDefaults.standard.set(birthdayTextField.text!, forKey: "birthday")
        // UserDefaults.standard.synchronize()
        
        nameLabel.text = "Name:\(nameTextField.text!)"
        birthdayLabel.text = "Birthday:\(birthdayTextField.text!)"
        
    }
        
        @IBAction func deleteClicked(_ sender: Any) {
            
            let storedName = UserDefaults.standard.object(forKey: "name")
            let storedBirthday = UserDefaults.standard.object(forKey: "birthday")
            
            // "" ( boş) vs. nil (tanımlanmamış yok demek)
            if (storedName as? String) != nil {
                UserDefaults.standard.removeObject(forKey: "name")
                nameLabel.text = "Name: "
                
            }
            
            if (storedBirthday as? String) != nil {
                UserDefaults.standard.removeObject(forKey: "birthday")
                birthdayLabel.text = "Birthday: "
            }
            
        }
    }
