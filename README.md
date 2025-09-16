# ================= Weather Record ADT =================
class WeatherRecord:
    def __init__(self, date="", city="", temperature=0.0):
        self.date = date        # format: DD/MM/YYYY
        self.city = city
        self.temperature = temperature


# ================= Data Storage Class =================
class WeatherDataStorage:
    def __init__(self, years, cities):
        self.years = years
        self.cities = cities
        self.SENTINEL = -9999   # for sparse data
        # 2D array: years x cities
        self.temperatureData = [
            [self.SENTINEL for _ in range(len(cities))]
            for _ in range(len(years))
        ]

    # Insert new record
    def insert(self, record: WeatherRecord):
        year = int(record.date[6:10])   # extract YYYY
        row = self.getYearIndex(year)
        col = self.getCityIndex(record.city)

        if row != -1 and col != -1:
            self.temperatureData[row][col] = record.temperature
        else:
            print("Invalid city or year!")

    # Delete record
    def remove(self, city, year):
        row = self.getYearIndex(year)
        col = self.getCityIndex(city)

        if row != -1 and col != -1:
            self.temperatureData[row][col] = self.SENTINEL

    # Retrieve city-wise data for a given year
    def retrieve(self, city, year):
        row = self.getYearIndex(year)
        col = self.getCityIndex(city)

        if row != -1 and col != -1:
            if self.temperatureData[row][col] != self.SENTINEL:
                print(
                    f"Temperature in {city} ({year}): {self.temperatureData[row][col]}°C"
                )
            else:
                print("No data available.")

    # Populate array with sample data
    def populateArray(self):
        for i in range(len(self.years)):
            for j in range(len(self.cities)):
                self.temperatureData[i][j] = (i + j) * 2 + 20  # dummy values

    # Row-major access
    def rowMajorAccess(self):
        print("\nRow-Major Traversal:")
        for i in range(len(self.years)):
            for j in range(len(self.cities)):
                print(
                    f"[{self.years[i]},{self.cities[j]}]: {self.temperatureData[i][j]}\t",
                    end="",
                )
            print()

    # Column-major access
    def columnMajorAccess(self):
        print("\nColumn-Major Traversal:")
        for j in range(len(self.cities)):
            for i in range(len(self.years)):
                print(
                    f"[{self.years[i]},{self.cities[j]}]: {self.temperatureData[i][j]}\t",
                    end="",
                )
            print()

    # Handle sparse data
    def handleSparseData(self):
        print("\nSparse Data Representation:")
        for i in range(len(self.years)):
            for j in range(len(self.cities)):
                if self.temperatureData[i][j] != self.SENTINEL:
                    print(
                        f"[{self.years[i]},{self.cities[j]}]: {self.temperatureData[i][j]}"
                    )

    # Analyze complexity
    def analyzeComplexity(self):
        print("\nTime Complexity:")
        print("Insert: O(1)\nRetrieve: O(1)\nDelete: O(1)")
        print("\nSpace Complexity:")
        print("O(n*m) where n = years, m = cities")

    # Helper functions
    def getCityIndex(self, city):
        if city in self.cities:
            return self.cities.index(city)
        return -1

    def getYearIndex(self, year):
        if year in self.years:
            return self.years.index(year)
        return -1


# ================= Main Function =================
if __name__ == "__main__":
    years = [2023, 2024, 2025]
    cities = ["Delhi", "Mumbai", "Chennai"]

    system = WeatherDataStorage(years, cities)

    # Populate dummy data
    system.populateArray()
    system.rowMajorAccess()
    system.columnMajorAccess()

    # Insert and retrieve
    r1 = WeatherRecord("01/01/2024", "Delhi", 28.5)
    system.insert(r1)
    system.retrieve("Delhi", 2024)

    # Sparse data handling
    system.remove("Mumbai", 2025)
    system.handleSparseData()

    # Complexity analysis
    system.analyzeComplexity()




    
#sub problem 1
 class WeatherRecord:
    def __init__(self, date="", city="", temperature=0.0):
        self.date = date
        self.city = city
        self.temperature = temperature



#sub problem 2
self.temperatureData = [
    [self.SENTINEL for _ in range(len(cities))]
    for _ in range(len(years))
]
 



#sub problem 3
 def rowMajorAccess(self):
    for i in range(len(self.years)):
        for j in range(len(self.cities)):
            print(f"[{self.years[i]},{self.cities[j]}]: {self.temperatureData[i][j]}\t", end="")
        print()

def columnMajorAccess(self):
    for j in range(len(self.cities)):
        for i in range(len(self.years)):
            print(f"[{self.years[i]},{self.cities[j]}]: {self.temperatureData[i][j]}\t", end="")
        print()




#sub problem 4
def handleSparseData(self):
    for i in range(len(self.years)):
        for j in range(len(self.cities)):
            if self.temperatureData[i][j] != self.SENTINEL:
                print(f"[{self.years[i]},{self.cities[j]}]: {self.temperatureData[i][j]}")




#sub problem 5
def analyzeComplexity(self):
    print("\nTime Complexity:")
    print("Insert: O(1)\nRetrieve: O(1)\nDelete: O(1)")
    print("\nSpace Complexity:")
    print("O(n*m) where n = years, m = cities")

