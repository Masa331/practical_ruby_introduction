# Ruby Scripting - working with CSVs

[Back to menu](README.md)

## Example files & Resources

- [Contacts sales](contacts_sales.csv)
- [Contacts sales with headers](contacts_sales_with_headers.csv)
- Find latest CSV documentation on ruby-lang.org

## 1 - Read CSV in console

Goal = read csv from ruby console

1. Open up terminal and navigate to directory with example files.
2. Fire up `irb` - you are now in Ruby REPL(console)
3. Require CSV library = `require 'csv'`
4. load csv row into variable = `contacts = CSV.read('./contacts_sales.csv')`
5. print out all contact names in file = `contacts.each { |contact| puts contact[0] }`

## 2 - create ruby script from steps above

Goal = script which prints out all names from file. The script has to be runnable with `ruby print_contacts_names.rb`

## 3 - read csv file with headers

Goal = Create script which prints contacts names from csv file with headers

To read file with headers:

```ruby
contacts = CSV.read('contacts_sales_with_headers.csv', headers: true)
parsed = contacts.map { |row| row.to_h }
```

## 4 - Filter out contacts without vatins

1. use select to filter contacts - https://ruby-doc.org/core-2.2.0/Array.html#method-i-select
2. Writing to a file:

```ruby
CSV.open('contacts_with_vatin.csv', 'wb') do |csv|
  csv << ['contact_name', 'vatin']

  contacts_with_vatin.each do |contact|
    csv << [contact['name'], contact['vatin']]
  end
end

```

3. Enjoy filtered contacts :)
