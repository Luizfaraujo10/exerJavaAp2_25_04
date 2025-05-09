Algoritmo classe BinomialDistribution:
    publico estatico final int COIN_TOSSES <- 100
    publico estatico final int LINES_IN_DIAGRAM <- 30

    privado int num
    privado double prob
    privado int result

    Algoritmo classe Coin:
        privado boolean head

        Algoritmo toss():
            double random <- Math.random()
            se prob >= random então:
                head <- true
            retorna head

   Algoritmo construtor BinomialDistribution(int n, double p):
        num <- n
        prob <- p
        result <- 0

   Algoritmo experiment():
        Coin coin <- new Coin()
        result <- 0
        para i <- 0 até (num - 1) passo 1 faça:
            coin.head <- false
            coin.toss()
            se coin.head == true então:
                result <- result + 1
        retorna result

   Algoritmo main(String[] args):
        se args.length < 3 então:
            retorna

        double p <- Double.parseDouble(args[0])
        double p2 <- Double.parseDouble(args[1])
        int m <- Integer.parseInt(args[2])

        BinomialDistribution dist <- new BinomialDistribution(COIN_TOSSES, p)
        DataList data <- new DataList()

        para i <- 0 até (m - 1) passo 1 faça:
            data.insert(dist.experiment())

        BinomialDistribution dist2 <- new BinomialDistribution(COIN_TOSSES, p2)
        DataList data2 <- new DataList()

        para i <- 0 até (m - 1) passo 1 faça:
            data2.insert(dist2.experiment())

        data <- data.add(data2)
        Imprima data
        data.printDiagram(LINES_IN_DIAGRAM, COIN_TOSSES)
