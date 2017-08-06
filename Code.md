# high-frequency
A app that makes loud noises 

import UIKit

import AVFoundation

class ViewController: UIViewController {

    var player: AVAudioPlayer?
    
    var name: String = ""
   
    @IBOutlet weak var Sound: UILabel!

    @IBOutlet weak var Text2: UILabel!
    
    @IBOutlet weak var Text: UITextField!
   
    @IBOutlet weak var Slider: UISlider!
    
    @IBOutlet weak var Slider2: UISlider!
    
    @IBOutlet weak var Activity: UIActivityIndicatorView!
    
    @IBAction func Stop(_ sender: Any) {
        
        Activity.stopAnimating()
        
        Text.textColor = UIColor.red
        
        Text.text = nil;
        
        name = Text.text!
        
        Text.text = "Stopped \(name)"
    
        player?.stop()
    }
    

    @IBAction func khz(_ sender: Any) {
        
        Activity.stopAnimating()
        
        Text.text = nil;
        
        name = Text.text!
        
        Text.text = "Playing: 8 kHz \(name)"
        
        Text.textColor = UIColor.blue
        
        Activity.startAnimating()
    
        guard let url = Bundle.main.url(forResource: "8000", withExtension: "wav") else {
            print("error")
            return
        }
            
            do {
                try AVAudioSession.sharedInstance().setCategory(AVAudioSessionCategoryPlayback)
                try AVAudioSession.sharedInstance().setActive(true)
                
                player = try AVAudioPlayer(contentsOf: url)
                guard let player = player else { return }
                
                player.numberOfLoops = -100
                player.play()
            } catch let error {
                print(error.localizedDescription)
                }
            
    }
    
    @IBAction func khz2(_ sender: Any) {
        
        Activity.stopAnimating()
        
        Text.text = nil;
        
        name = Text.text!
        
        Text.text = "Playing: 12 kHz \(name)"
        
        Text.textColor = UIColor.blue
        
        Activity.startAnimating()
        
        guard let url = Bundle.main.url(forResource: "12000", withExtension: "wav") else {
            print("error")
            return
        }
        
        do {
            try AVAudioSession.sharedInstance().setCategory(AVAudioSessionCategoryPlayback)
            try AVAudioSession.sharedInstance().setActive(true)
            
            player = try AVAudioPlayer(contentsOf: url)
            guard let player = player else { return }
            
            player.numberOfLoops = -100
            player.play()
        } catch let error {
            print(error.localizedDescription)
        }
    }
    
    @IBAction func khz3(_ sender: Any) {
        
        Activity.stopAnimating()
        
        Text.text = nil;
        
        name = Text.text!
        
        Text.text = "Playing: 15 kHz \(name)"
        
        Text.textColor = UIColor.blue
        
        Activity.startAnimating()
        
        guard let url = Bundle.main.url(forResource: "15000", withExtension: "wav") else {
            print("error")
            return
        }
        
        do {
            try AVAudioSession.sharedInstance().setCategory(AVAudioSessionCategoryPlayback)
            try AVAudioSession.sharedInstance().setActive(true)
            
            player = try AVAudioPlayer(contentsOf: url)
            guard let player = player else { return }
            
            player.numberOfLoops = -100
            player.play()
        } catch let error {
            print(error.localizedDescription)
        }
    }
    
    @IBAction func khz4(_ sender: Any) {
        
        Activity.stopAnimating()
        
        Text.text = nil;
        
        name = Text.text!
        
        Text.text = "Playing: 16 kHz \(name)"
        
        Text.textColor = UIColor.blue
        
        Activity.startAnimating()
        
        guard let url = Bundle.main.url(forResource: "16000", withExtension: "wav") else {
            print("error")
            return
        }
        
        do {
            try AVAudioSession.sharedInstance().setCategory(AVAudioSessionCategoryPlayback)
            try AVAudioSession.sharedInstance().setActive(true)
            
            player = try AVAudioPlayer(contentsOf: url)
            guard let player = player else { return }
            
            player.numberOfLoops = -100
            player.play()
        } catch let error {
            print(error.localizedDescription)
        }
    }
   
    @IBAction func khz5(_ sender: Any) {
        
        Activity.stopAnimating()
        
        Text.text = nil;
        
        name = Text.text!
        
        Text.text = "Playing: 17 kHz \(name)"
        
        Text.textColor = UIColor.blue
        
        Activity.startAnimating()
        
        guard let url = Bundle.main.url(forResource: "17000", withExtension: "wav") else {
            print("error")
            return
        }
        
        do {
            try AVAudioSession.sharedInstance().setCategory(AVAudioSessionCategoryPlayback)
            try AVAudioSession.sharedInstance().setActive(true)
            
            player = try AVAudioPlayer(contentsOf: url)
            guard let player = player else { return }
            
            player.numberOfLoops = -100
            player.play()
        } catch let error {
            print(error.localizedDescription)
        }
    }

    @IBAction func About(_ sender: Any) {
        
        player?.stop()
        
        Text.text = nil;
        
        Text.textColor = UIColor.blue
        
        let alert = UIAlertController(title: "About", message: "Created On 7/7/2017, By: Sam Errett", preferredStyle:UIAlertControllerStyle.alert)
        alert.addAction(UIAlertAction(title: "Got It", style: UIAlertActionStyle.default, handler: nil))
        self.present(alert, animated: true, completion: nil)
    }
    
    @IBAction func audioslider(_ sender: Any) {
        
        player?.pan = Slider2.value
        
        let x = Slider2.value
        
        let myNum = (x * 100).rounded() / 1
        
        Sound.text = "L / R: \(myNum)"
    
    }

    @IBAction func ChangeAudioTime(_ sender: Any) {
        
        player?.volume = Slider.value
        
        let currentValue = Int(Slider.value)
        Text2.text = "Volume: \(currentValue) %"
    }
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let audioSession = AVAudioSession.sharedInstance()
        do {
            try audioSession.setCategory(AVAudioSessionCategoryPlayback, with: [.mixWithOthers])
            try audioSession.setActive(true)
        }catch{
            
        }
        
    }
}
