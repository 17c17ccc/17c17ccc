在当今的数字化时代，管理库存变得越来越重要。为了有效地管理衬衣库存，我们可以编写一个简单的软件应用。本文将介绍如何使用Python编写一个基本的衬衣管理软件，涵盖衬衣的添加、删除、更新和查询功能。

1. 环境准备
首先，确保你已经安装了Python。如果没有安装，可以从Python官网下载并安装最新版本的Python。

2. 定义数据结构
为了存储衬衣信息，我们将使用一个列表，每个元素是一个包含衬衣详情的字典。

python
shirts = []
3. 添加衬衣（Create）
我们将定义一个函数来添加新的衬衣到库存中。每个衬衣包含id、brand、size和quantity等信息。

python
def add_shirt(shirt_id, brand, size, quantity):
    shirt = {
        'id': shirt_id,
        'brand': brand,
        'size': size,
        'quantity': quantity
    }
    shirts.append(shirt)
    print(f"Shirt {shirt_id} added successfully.")
4. 查询衬衣（Read）
我们可以定义一个函数来显示所有衬衣信息，或者根据特定ID查询单个衬衣信息。

python
def list_shirts():
    if not shirts:
        print("No shirts available.")
    else:
        for shirt in shirts:
            print(shirt)
 
def find_shirt(shirt_id):
    for shirt in shirts:
        if shirt['id'] == shirt_id:
            return shirt
    print(f"Shirt with ID {shirt_id} not found.")
    return None
5. 更新衬衣（Update）
定义一个函数来更新库存中的衬衣信息。

python
def update_shirt(shirt_id, new_data):
    shirt = find_shirt(shirt_id)
    if shirt:
        shirt.update(new_data)
        print(f"Shirt {shirt_id} updated successfully.")
    else:
        print(f"Shirt with ID {shirt_id} not found.")
6. 删除衬衣（Delete）
定义一个函数来从库存中删除特定ID的衬衣。

python
def delete_shirt(shirt_id):
    global shirts
    shirts = [shirt for shirt in shirts if shirt['id'] != shirt_id]
    print(f"Shirt {shirt_id} deleted successfully.")
7. 主菜单
最后，我们定义一个主菜单函数，让用户可以选择执行不同的操作。

python
def main_menu():
    while True:
        print("\nShirt Management Software")
        print("1. Add Shirt")
        print("2. List Shirts")
        print("3. Find Shirt by ID")
        print("4. Update Shirt")
        print("5. Delete Shirt")
        print("6. Exit")
        
        choice = input("Enter your choice: ")
        
        if choice == '1':
            shirt_id = input("Enter shirt ID: ")
            brand = input("Enter brand: ")
            size = input("Enter size: ")
            quantity = int(input("Enter quantity: "))
            add_shirt(shirt_id, brand, size, quantity)
        elif choice == '2':
            list_shirts()
        elif choice == '3':
            shirt_id = input("Enter shirt ID to find: ")
            find_shirt(shirt_id)
        elif choice == '4':
            shirt_id = input("Enter shirt ID to update: ")
            new_brand = input("Enter new brand (leave blank to keep current): ") or None
            new_size = input("Enter new size (leave blank to keep current): ") or None
            new_quantity = input("Enter new quantity (leave blank to keep current): ")
            if new_quantity:
                new_quantity = int(new_quantity)
            else:
                new_quantity = None
            
            new_data = {}
            if new_brand:
                new_data['brand'] = new_brand
            if new_size:
                new_data['size'] = new_size
            if new_quantity is not None:
                new_data['quantity'] = new_quantity
            
            update_shirt(shirt_id, new_data)
        elif choice == '5':
            shirt_id = input("Enter shirt ID to delete: ")
            delete_shirt(shirt_id)
        elif choice == '6':
            print("Exiting the software.")
            break
        else:
            print("Invalid choice. Please try again.")
 
if __name__ == "__main__":
    main_menu()
8. 运行程序
将上述代码保存为一个Python文件（例如shirt_management.py），然后在终端或命令行中运行该文件：

bash
python shirt_management.py
你将看到一个简单的文本菜单，允许你添加、查询、更新和删除衬衣库存。

总结
本文介绍了如何使用Python编写一个简单的衬衣管理软件，涵盖了基本的CRUD操作。这个示例是一个起点，你可以根据需要扩展功能，比如添加更多的衬衣属性、持久化数据到数据库、提供图形用户界面等。希望这个例子对你有所帮助！
