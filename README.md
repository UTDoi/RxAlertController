RxAlertController
====

RxAlertController is UIAlertController-Extension, which integrates UIAlertController and UIAlertAction into your Rx-Project.

I made this Extension referencing the article below.

[RxSwift UIAlertController を observable で表示](https://qiita.com/katafuchix/items/50266e0eb52a032c9629)


## Requirement
- RxSwift
- RxCocoa

## Usage

1. make AlertActions with titles
2. make UIAlertController by using static method "showAlert", which returns Observable<Int> (index of selected action)
3. implement methods of selected actions in subscribe

Example:
```
 let actions = [AlertAction.action(title: ""), AlertAction.action(title: "")]
 
 addButton.rx.tap
            .flatMap { UIAlertController.showAlert(from: self, title: "", message: "", style: .alert, actions: actions) }
            .subscribe(onNext: { index in
                if index == 0 {
                    print("action1")
                } else {
                    print("action2")
                }
            })
            .disposed(by: disposeBag)
```

## Licence

[MIT](https://github.com/UTDoi/RxAlertController/blob/master/LICENSE)

## Author

[UTDoi](https://github.com/UTDoi)
