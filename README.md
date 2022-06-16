# 14-homework

이 장에서는 아이폰 앱에서 비디오 파일을 재생하는 방법에 대해 알아보겠습니다. 애플 iOS에서 제공하는 AVPlayerViewController를 사용하면 앱 내부에 저장되어 있는 비디오 파일뿐만 아니라 외부에 링크된 비디오 파일도 간단하게 재생할 수 있습니다.

비디오 플레이어는 아이폰 사용자들이 가장 많이 사용하는 앱 중의 하나입니다. 등하굣길이나 출퇴근길에 영화를 감상하거나 동영상 강좌를 듣는 사용자들을 쉽게 볼 수 있습니다. 아이폰에서의 비디오 재생 방법을 잘 활용하면 다음과 같은 비디오 재생 앱도 만들 수 있습니다.

```
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

