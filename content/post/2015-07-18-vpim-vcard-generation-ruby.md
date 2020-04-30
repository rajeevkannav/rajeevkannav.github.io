---
layout: post
title: "ruby vpim library generate expendable vcard"
modified: 2015-07-18
excerpt: "vpim generating vcard with more capabilities."
tags: [vpim,vcard,ruby]
comments: true
---

### Create VCardField to have more capabilities

![Target](./../images/vcard.png)


Subclass of Vpim::DirectoryInfo::Field adds a number of helpful methods for creating VCard fields.

{% highlight ruby %}

require 'vpim/vcard'

class VCardField < Vpim::DirectoryInfo::Field

  def VCardField.reset_custom_fields
    @@custom_number = 1
  end

  #
  # Create a name field: "N"
  #
  def VCardField.create_n (last, first=nil, middle=nil, prefix=nil, suffix=nil)
    VCardField.create('N', "#{last};#{first};#{middle};#{prefix};#{suffix}")
  end

  protected
  
  def VCardField.valid_string(a_str)
    return a_str != nil && a_str.length > 0
  end

  public

  #
  # Create a formal name field: "FN"
  #
  def VCardField.create_fn (last, first=nil, middle=nil, prefix=nil, suffix=nil)
    name = ""
    if valid_string(prefix) then
      name << "#{prefix} "
    end
    if valid_string(first) then
      name << "#{first} "
    end
    if valid_string(middle) then
      name << "#{middle} "
    end
    if valid_string(last) then
      name << "#{last} "
    end
    if valid_string(suffix) then
      name << "#{suffix} "
    end
    VCardField.create('FN', "#{name}")
  end

  #
  # Create a formal name field: "ORG"
  #
  def VCardField.create_org (organization_name, department_name=nil)
    VCardField.create("ORG", "#{organization_name};#{department_name}")
  end

  #
  # Create a title field: "TITLE"
  #
  def VCardField.create_job_title(title)
    VCardField.create("TITLE", title)
  end

  #
  # Create an email field: "EMAIL" with type="INTERNET"
  #
  # For _type_, use Ruby symbols :WORK or :HOME.
  #
  def VCardField.create_internet_email(address, type=:WORK, preferred_email=false)
    if preferred_email == true
      VCardField.create("EMAIL", address,
                        "type" => ["INTERNET", type.to_s, "pref"])
    else
      VCardField.create("EMAIL", address,
                        "type" => ["INTERNET", type.to_s])
    end
  end

  protected
  def VCardField.next_custom_name
    name = "item#{@@custom_number}"
    @@custom_number = @@custom_number + 1
    name
  end

  def VCardField.create_phone(phone_num, is_preferred = false, type_arr = ["WORK"],
      custom_name = nil)

    field_name = ""
    if custom_name != nil
      field_name << next_custom_name
      field_name << "."
    end

    # Flatten the array so we can add additional items to it.
    type_arr = [type_arr].flatten
    # If this phone number is preferred, then add that into the type array.
    if is_preferred
      type_arr << "pref"
    end
    # Create the TEL field.
    ret_val = [VCardField.create("#{field_name}TEL", phone_num, "type" => type_arr)]
    # If we need a custom field . . .
    if custom_name != nil
      ret_val << VCardField.create("#{field_name}X-ABLabel", custom_name)
    end
    ret_val
  end

  public
  
  def VCardField.create_note(note_text)
    VCardField.create("NOTE", note_text)
  end

  def VCardField.create_custom_phone(phone_number, custom_name, is_preferred = false)
    VCardField.create_phone(phone_number, is_preferred, ["HOME"], custom_name)
  end

  def VCardField.create_pager(pager_number, is_preferred = false)
    VCardField.create_phone(pager_number, is_preferred, ["PAGER"])
  end

  def VCardField.create_work_fax(fax_number, is_preferred = false)
    VCardField.create_phone(fax_number, is_preferred, ["FAX", "WORK"])
  end

  def VCardField.create_work_phone(phone_number, is_preferred = false)
    VCardField.create_phone(phone_number, is_preferred, ["WORK"])
  end

  def VCardField.create_home_fax(fax_number, is_preferred = false)
    VCardField.create_phone(fax_number, is_preferred, ["FAX", "HOME"])
  end

  def VCardField.create_home_phone(phone_number, is_preferred = false)
    VCardField.create_phone(phone_number, is_preferred, ["HOME"])
  end

  def VCardField.create_cell_phone(phone_number, is_preferred = false)
    VCardField.create_phone(phone_number, is_preferred, ["CELL"])
  end
  
  def VCardField.create_work_email(address, is_preferred = false)
    VCardField.create_email(address, is_preferred, ["WORK"])
  end

  def VCardField.create_home_email(address, is_preferred = false)
    VCardField.create_email(address, is_preferred, ["HOME"])
  end

  def VCardField.create_other_email(address, custom_name, is_preferred = false)
    VCardField.create_email(address, is_preferred, ["WORK"], custom_name)
  end

  protected
  
  def VCardField.create_email(address, is_preferred, type_arr = ["WORK"], custom_name = nil)
    name = ""
    if custom_name != nil
      name << next_custom_name
      name << "."
    end
    if is_preferred
      type_arr << "pref"
    end
    ret_val = [VCardField.create("#{name}EMAIL", address, "type" => type_arr)]
    if custom_name != nil
      ret_val << VCardField.create("#{name}X-ABLabel", custom_name)
    end
    ret_val
  end

end

info = { 
 title: 'Mr./Mrs',
 display_name: 'Card Holder Name',
 email: 'email@example.com',
 note: 'Note 1', 
 first_name: 'Card Holder FirstName',
 office_phone: '123456789',
 fax_phone: '123456789',
 home_phone: '123456789',
 mobile_phone: '123456789'
}
 

vcard = Vpim::Vcard.create
vcard << VCardField.create_job_title(info[:title])
vcard << VCardField.create_n(info[:display_name])
vcard << VCardField.create_work_email(info[:email])
vcard << VCardField.create_note(info[:note]) 
vcard << VCardField.create_fn(info[:first_name])
vcard << VCardField.create_work_phone(info[:office_phone]) 
vcard << VCardField.create_work_fax(info[:fax_phone]) 
vcard << VCardField.create_home_phone(info[:home_phone]) 
vcard << VCardField.create_cell_phone(info[:mobile_phone]) 
vcard.each { |card|
	puts card.to_s
}


{% endhighlight %}

[Source] (https://github.com/xing/vpim/blob/master/samples/tabbed-file-to-vcf.rb)

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>