
### Tableview cell life cycle 


```
oldIndexPath: nil
cellForRowAt: 0
willDisplay: 0
oldIndexPath: nil
cellForRowAt: 1
willDisplay: 1
oldIndexPath: nil
cellForRowAt: 2
willDisplay: 2
oldIndexPath: nil
cellForRowAt: 3
willDisplay: 3
oldIndexPath: nil
cellForRowAt: 4
willDisplay: 4
oldIndexPath: nil
cellForRowAt: 5
willDisplay: 5
oldIndexPath: nil
cellForRowAt: 6
willDisplay: 6
oldIndexPath: nil
cellForRowAt: 7
willDisplay: 7
oldIndexPath: nil
cellForRowAt: 8
willDisplay: 8
oldIndexPath: nil
cellForRowAt: 9
willDisplay: 9
oldIndexPath: nil
cellForRowAt: 10
willDisplay: 10
oldIndexPath: nil
cellForRowAt: 11
willDisplay: 11
oldIndexPath: nil
cellForRowAt: 12
willDisplay: 12
oldIndexPath: nil
cellForRowAt: 13
willDisplay: 13
oldIndexPath: nil
cellForRowAt: 14
willDisplay: 14
oldIndexPath: nil
cellForRowAt: 15
willDisplay: 15
oldIndexPath: nil
cellForRowAt: 16
willDisplay: 16
oldIndexPath: nil
cellForRowAt: 17
willDisplay: 17
oldIndexPath: nil
cellForRowAt: 18
willDisplay: 18
oldIndexPath: nil
cellForRowAt: 19
willDisplay: 19
oldIndexPath: nil
cellForRowAt: 20
willDisplay: 20
oldIndexPath: nil
cellForRowAt: 21
didEndDisplaying: 0
willDisplay: 21
oldIndexPath: nil
cellForRowAt: 22
didEndDisplaying: 1
willDisplay: 22
prepareForReuse: Optional(0)
oldIndexPath: Optional(0)
cellForRowAt: 23
didEndDisplaying: 2
willDisplay: 23
prepareForReuse: Optional(1)
oldIndexPath: Optional(1)
cellForRowAt: 24
didEndDisplaying: 3
willDisplay: 24
prepareForReuse: Optional(2)
oldIndexPath: Optional(2)
cellForRowAt: 25
didEndDisplaying: 4
willDisplay: 25
prepareForReuse: Optional(3)
oldIndexPath: Optional(3)
cellForRowAt: 26
didEndDisplaying: 5
willDisplay: 26
prepareForReuse: Optional(4)
oldIndexPath: Optional(4)
cellForRowAt: 27
didEndDisplaying: 6
willDisplay: 27
prepareForReuse: Optional(5)
oldIndexPath: Optional(5)
cellForRowAt: 28
didEndDisplaying: 7
```



```

    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        self.countries.count
    }

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "CountryCell", for: indexPath) as! CountryTableViewCell

        let country = self.countries[indexPath.row]
        cell.textLabel?.text = country.name
        cell.detailTextLabel?.text = country.isoCode
        cell.imageView?.image = UIImage(named: country.isoCode)
        print("oldIndexPath: \(cell.indexPath?.row)")
        cell.indexPath = indexPath
        print("cellForRowAt: \(indexPath.row)")
        return cell
    }

    override func tableView(_ tableView: UITableView, titleForHeaderInSection section: Int) -> String? {
        "Countries"
    }

    override func tableView(_ tableView: UITableView, willDisplay cell: UITableViewCell, forRowAt indexPath: IndexPath) {
        (cell as? CountryTableViewCell)?.indexPath = indexPath
        print("willDisplay: \(indexPath.row)")
    }

    override func tableView(_ tableView: UITableView, didEndDisplaying cell: UITableViewCell, forRowAt indexPath: IndexPath) {
        print("didEndDisplaying: \(indexPath.row)")
    }
}

final class CountryTableViewCell: UITableViewCell {

    var indexPath: IndexPath?

    override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
        super.init(style: UITableViewCell.CellStyle.default, reuseIdentifier: reuseIdentifier)
    }

    required init?(coder: NSCoder) {
        super.init(coder: coder)
    }

    override func prepareForReuse() {
        print("prepareForReuse: \(indexPath?.row)")
    }
}

```
