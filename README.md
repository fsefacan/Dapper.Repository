# Dapper.Repository
Dapper Sql Query Generator with Repository Design Pattern

No major changes will be made except for the existing features.

We've done this to make your small and repetitive tasks easier.

Relational table query(join, lazy loading) etc. will not be added.

If we want our code to run fast, we have to do our big business manually and consciously.

# Usage
````
class Program
    {
        static void Main(string[] args)
        {
            var productRepository = new Repository<Product>();

            var product = new Product
            {
                Name = "Ipad Pro 13 inch 64 GB",
                Price = 2480m,
                CreatedDate = DateTime.Now
            };

            //insert
            productRepository.Insert(product);

            //find by identifier
            product = productRepository.Find(product.Id);
            product.Price = 2999m;

            //update
            productRepository.Update(product);

            //delete
            productRepository.Delete(product);

            //find all with expression
            var products = productRepository.FindAll(x => x.Published || x.DisplayOrder != 0);
            foreach (var item in products)
            {
                Console.WriteLine("Found: {0} - {1}", item.Name, item.Price);
            }

            Console.ReadKey();
        }
    }
