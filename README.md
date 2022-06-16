# 14-homework

//
//  ViewController.swift
//  MoviePlayer
//
// Created by 203a06 on 2022/05/27.
// 202116019 유정훈

 
 
 import UIKit
 import AVKit

 class ViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
    }

    @IBAction func btnPlayInternalMovie(_ sender: UIButton) {
        //내부 파일 mp4
        let filePath:String? = Bundle.main.path(forResource: "fastTyping", ofType: "mp4")
        //앱 내부의 파일명을 NSURL 형식으로 변경
        let url = NSURL(fileURLWithPath: filePath!)
        
        playVideo(url: url) //앞에서 얻은 url을 사용하여 비디오를 재생
        
        }
        

    func btnPlayerExternalMovie(_ sender: UIButton) {
        //외부 파일 mp4
    let url=NSURL(string:"https://dl.dropboxusercontent.com/s/e38auz050w2mvud/Fireworks.mp4")!
        
        playVideo(url: url) //앞에서 얻은 url을 사용하여 비디오를 재생

       
        }
    
    
    
    private func playVideo(url: NSURL) {
    //AVPlayerViewController의 인스턴스를 생성
        let playerController = AVPlayerViewController()
    //비디오 URL로 초기화된 AVPlayer의 인스턴스를 생성
        let player = AVPlayer(url: url as URL)
        //AVPlayerViewController의 player 속성에 위에서 생성한 AVPlayer 인스턴스를 할당
        playerController.player = player
        
        self.present(playerController, animated: true) {
            player.play() //비디오 재생
        }
        
    }
    
}

