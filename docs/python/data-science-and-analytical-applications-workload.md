---
title: Pracovní zátěž pro datové vědy a analytické aplikace
description: Tato úloha Visual Studia sdružuje Python, F# a jejich příslušné distribuce za běhu včetně Anaconda. (R je také součástí visual studio 2017 pouze.)
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44906d70be05891fe52096adec2f61f2261b5db5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "70154882"
---
# <a name="install-data-science-support-in-visual-studio"></a>Instalace podpory datových věd v sadě Visual Studio

Zatížení datové vědy a analytických aplikací, které vyberete a nainstalujete prostřednictvím instalačního programu sady Visual Studio, sdružuje několik jazyků a jejich příslušné distribuce za běhu:

::: moniker range="vs-2017"
- [Python a Anakonda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# s rozhraním .NET](/dotnet/fsharp/)
- [R a Microsoft R klienta](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# s rozhraním .NET](/dotnet/fsharp/)
::: moniker-end

![Úlohy aplikací pro datové vědy a analýzy v instalačním programu Sady Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python a R jsou dva z primárních skriptovacích jazyků používaných pro datové vědy. Oba jazyky se snadno učí a jsou podporovány bohatým ekosystémem balíčků. Tyto balíčky řeší širokou škálu scénářů, jako je získávání dat, čištění, školení modelu, nasazení a vykreslování. F# je také výkonný funkční první jazyk .NET, který je vhodný pro širokou škálu úloh zpracování dat.
::: moniker-end

::: moniker range="vs-2019"
Python je primární skriptovací jazyk používaný pro datové vědy. Python se snadno učí a je podporován bohatým ekosystémem balíčků. Tyto balíčky řeší širokou škálu scénářů, jako je získávání dat, čištění, školení modelu, nasazení a vykreslování. F# je také výkonný funkční první jazyk .NET, který je vhodný pro širokou škálu úloh zpracování dat. (Pro jazyk R doporučujeme [Poznámkové bloky Azure](https://notebooks.azure.com).)
::: moniker-end

<!--Note link on the image because this one is large -->
[![Snímky obrazovky sady Visual Studio s R, Pythonem a F #](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Možnosti pracovního vytížení

Ve výchozím nastavení pracovní vytížení nainstaluje následující možnosti, které můžete upravit v souhrnné části pro úlohy v instalačníslužbě sady Visual Studio:

::: moniker range="vs-2019"
- Podpora jazyka pro stolní počítače F#
- Python:
  - Podpora jazyka Pythonu
  - Webová podpora pythonu
::: moniker-end

::: moniker range="vs-2017"
- Podpora jazyka F#
- Python:
  - Podpora jazyka Pythonu
  - [Anaconda3 64-bit](https://www.continuum.io), distribuce Pythonu, která zahrnuje rozsáhlé knihovny datových věd a interpret pythonu.
  - Webová podpora pythonu
  - Podpora pro Cookiecutter template
- R:
  - Podpora jazyka R
  - Podpora runtime pro vývojové nástroje R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (Microsoft je plně kompatibilní, komunitou podporované R interpret s knihovnami ScaleR pro rychlejší výpočty na jednotlivých uzlech nebo clusterech. Můžete také použít libovolné R z [CRAN](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integrace SQL Serveru

::: moniker range="vs-2017"
SQL Server podporuje použití Pythonu i R k provádění pokročilých analýz přímo uvnitř SQL Serveru. R podpora je součástí SQL Server 2016 a novější; Podpora Pythonu je dostupná v SQL Serveru 2017 CTP 2.0 a novějším.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server podporuje použití Pythonu k provádění pokročilých analýz přímo uvnitř SQL Serveru. Podpora Pythonu je dostupná v SQL Serveru 2017 CTP 2.0 a novějším.
::: moniker-end

Můžete využívat následující výhody spuštěním kódu, kde vaše data již žije:

- **Eliminace přesunu dat**: Namísto přesunutí dat z databáze do aplikace nebo modelu můžete vytvářet aplikace v databázi. Tato funkce odstraňuje překážky zabezpečení, dodržování předpisů, zásad správného řízení, integrity a řadu podobných problémů souvisejících s přesouváním obrovského množství dat. Můžete také využívat datové sady, které se nevešly do paměti klientského počítače.

- **Snadné nasazení**: Jakmile máte připravený model, nasazení do produkčního prostředí je jednoduchá záležitost jeho vložení do skriptu T-SQL. Každá klientská aplikace SQL napsaná v libovolném jazyce pak může využít modely a inteligenci prostřednictvím volání uložené procedury. Nejsou nutné žádné konkrétní jazykové integrace.

- **Výkon a škálování na podnikové úrovni**: Pokročilé funkce serveru SQL Server, jako jsou indexy úložiště tabulek a sloupců v paměti, můžete použít s vysoce výkonnými škálovatelnými platformami API v balíčcích RevoScale. Odstranění přesunu dat také znamená, že se vyhnete omezením paměti klienta, protože data rostou nebo chcete zvýšit výkon aplikace.

- **Rich rozšiřitelnost**: Můžete nainstalovat a spustit některý z nejnovějších balíčků s otevřeným zdrojovým kódem v SQL Serveru k vytvoření hluboké učení a AI aplikace na obrovské množství dat v SQL Server. Instalace balíčku v SQL Serveru je stejně jednoduchá jako instalace balíčku do místního počítače.

- **Široká dostupnost bez dalších nákladů**: Jazykové integrace jsou k dispozici ve všech edicích SQL Serveru 2017 a novějších, včetně edice Express.

Chcete-li plně využít výhod integrace serveru SQL Server, nainstalujte pomocí instalačního programu sady Visual Studio **úlohu úložiště dat a zpracování** pomocí možnosti Nástroje pro data serveru SQL **Server.** Druhá možnost umožňuje SQL IntelliSense, zvýraznění syntaxe a nasazení.

![Úloha pro ukládání a zpracování dat](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Možnosti úlohy ukládání a zpracování dat](media/workload/data-storage-workload-options.png)

Další informace najdete tady:

::: moniker range="vs-2017"
- [Práce se servery SQL Server a R](../rtvs/integrating-sql-server-with-r.md)
- [In-database Advanced Analytics with R v SQL Serveru 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python v SQL Serveru 2017: vylepšené strojové učení v databázi (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Doplňkové služby a sady SDK

Kromě toho, co je přímo v zatížení aplikací pro datové vědy a analýzy, jsou služba Azure Notebooks a Sada Azure SDK pro Python také užitečné pro datové vědy.

Sada Azure SDK pro Python usnadňuje využití a správu služeb Microsoft Azure z aplikací spuštěných na Windows, Macu a Linuxu. Další informace naleznete v [tématu Azure SDK pro Python](/azure/python/).

Poznámkové bloky Azure (aktuálně ve verzi Preview) poskytují bezplatný online přístup k poznámkovým blokům Jupyter, které běží v cloudu v Microsoft Azure. Služba obsahuje ukázkové poznámkové bloky v Pythonu, R a F#, které vám pomohou začít. Navštivte [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Snímky obrazovky poznámkových bloků Azure s ukázkou Úvod do R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
