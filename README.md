Data Analyst Portfolio Project Repository
This Repository will hold all of the code and queries from the Portfolio Projects I create.

Please feel free to take these and run with them. Make them your own and find your own insights

@@ -25,10 +25,10 @@ and continent is not null
ORDER BY 1,2


-- Total Cases vs Population
-- Shows what percentage of population infected with Covid


-- Total Cases vs Population
-- Shows what percentage of population infected with Covid

SELECT location, date,population total_cases, (total_cases/population)*100 AS PercentPopulationInfected
FROM PortfolioProject..CovidDeaths
@@ -55,8 +55,8 @@ WHERE continent is not null
GROUP BY location
ORDER BY TotalDeathsCount DESC	

-- BREAKING IT DOWN BY CONTINENT

-- BREAKING IT DOWN BY CONTINENT
-- Showing contintents with the highest death count per population

SELECT location, MAX(cast(total_deaths as int)) AS TotalDeathsCount
@@ -67,18 +67,18 @@ GROUP BY location
ORDER BY TotalDeathsCount DESC	


-- Showing contintents with the highest death count per population

Select continent, MAX(cast(Total_deaths as int)) as TotalDeathCount
From PortfolioProject..CovidDeaths
--Where location like '%Nigeria%''
Where continent is not null 
Group by continent
order by TotalDeathCount desc


-- GLOBAL NUMBERS

-- Showing contintents with the highest death count per population
Select continent, MAX(cast(Total_deaths as int)) as TotalDeathCount
From PortfolioProject..CovidDeaths
--Where location like '%Nigeria%''
Where continent is not null 
Group by continent
order by TotalDeathCount desc
-- GLOBAL NUMBERS

SELECT SUM(new_cases) AS Total_cases, SUM(cast(new_deaths as int)) AS Total_Deaths, SUM(cast(new_deaths as int))/ SUM(new_cases)*100 AS DeathsPercentage
FROM PortfolioProject..CovidDeaths
@@ -88,10 +88,10 @@ WHERE continent is not null
ORDER BY 1,2



-- Total Population vs Vaccinations
-- Shows Percentage of Population that has recieved at least one Covid Vaccine

-- Total Population vs Vaccinations
-- Shows Percentage of Population that has recieved at least one Covid Vaccine
SELECT dea.continent, dea.location, dea.date,dea.population, vac.new_vaccinations, 
SUM(CONVERT(int,vac.new_vaccinations)) OVER (partition by dea.location order by dea.location, dea.date) AS RollingPeopleVaccinated
FROM PortfolioProject..CovidDeaths dea
@@ -183,17 +183,17 @@ WHERE continent is not null


--- VIEW 3 Deaths By Continent

CREATE VIEW Death_by_Continent AS
Select continent, MAX(cast(Total_deaths as int)) as TotalDeathCount
From PortfolioProject..CovidDeaths
--Where location like '%Nigeria%''
Where continent is not null 
Group by continent
--order by TotalDeathCount desc


--VIEW 4 contintents with the highest death count per population

CREATE VIEW CountryWithHighestDeaths AS
Select continent, MAX(cast(Total_deaths as int)) as TotalDeathCount
From PortfolioProject..CovidDeaths
--Where location like '%Nigeria%''
Where continent is not null 
Group by continent
--order by TotalDeathCount desc


--VIEW 4 contintents with the highest death count per population
CREATE VIEW CountryWithHighestDeaths AS
SELECT location, MAX(cast(total_deaths as int)) AS TotalDeathsCount
FROM PortfolioProject..CovidDeaths
--where location like '%Nigeria'
@@ -220,9 +220,9 @@ FROM HighestInfectionRate



-- VIEW 6 Total cases & population percentage infected


-- VIEW 6 Total cases & population percentage infected
CREATE VIEW TotalCasesPercentageInfected AS
SELECT location, date,population total_cases, (total_cases/population)*100 AS PercentPopulationInfected
FROM PortfolioProject..CovidDeaths
