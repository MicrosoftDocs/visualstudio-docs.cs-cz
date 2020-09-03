---
title: Úlohy pro datové vědy a analytické aplikace
description: 'Tato úloha sady Visual Studio přináší dohromady Python, F # a jejich příslušné distribuce modulu runtime, včetně Anaconda. (R je také součástí sady Visual Studio 2017.)'
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44906d70be05891fe52096adec2f61f2261b5db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "70154882"
---
# <a name="install-data-science-support-in-visual-studio"></a>Instalace podpory pro datové vědy v aplikaci Visual Studio

Úloha aplikace pro datovou vědu a analýzu, kterou vyberete a nainstalujete prostřednictvím instalačního programu sady Visual Studio, spojuje několik jazyků a jejich příslušné distribuce modulu runtime:

::: moniker range="vs-2017"
- [Python a Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F # s rozhraním .NET Framework](/dotnet/fsharp/)
- [R a Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F # s rozhraním .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Úlohy pro datové vědy a analytické aplikace v instalačním programu sady Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
Python a R jsou dva z primárních skriptovacích jazyků používaných pro datové vědy. Oba jazyky se snadno učí a podporují bohatý ekosystém balíčků. Tyto balíčky řeší široké spektrum scénářů, jako jsou získávání dat, čištění, školení modelů, nasazování a vykreslování. F # je také výkonný funkční jazyk .NET, který je vhodný pro širokou škálu úloh zpracování dat.
::: moniker-end

::: moniker range="vs-2019"
Python je primární skriptovací jazyk používaný pro datové vědy. Python se snadno učí a podporuje bohatý ekosystém balíčků. Tyto balíčky řeší široké spektrum scénářů, jako jsou získávání dat, čištění, školení modelů, nasazování a vykreslování. F # je také výkonný funkční jazyk .NET, který je vhodný pro širokou škálu úloh zpracování dat. (Pro jazyk R doporučujeme [Azure Notebooks](https://notebooks.azure.com).)
::: moniker-end

<!--Note link on the image because this one is large -->
[![Snímky obrazovky sady Visual Studio s R, Pythonem a F #](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Možnosti úlohy

Ve výchozím nastavení zatížení nainstaluje následující možnosti, které můžete upravit v části Souhrn pro úlohu v instalačním programu sady Visual Studio:

::: moniker range="vs-2019"
- Podpora jazyka F # pro Desktop
- Python:
  - Podpora jazyka Python
  - Podpora webu Pythonu
::: moniker-end

::: moniker range="vs-2017"
- Podpora jazyka F #
- Python:
  - Podpora jazyka Python
  - [Anaconda3 64-bit](https://www.continuum.io), distribuce Pythonu, který obsahuje rozsáhlé knihovny pro datové vědy a interpret Pythonu.
  - Podpora webu Pythonu
  - Podpora šablon Cookiecutter
- Í
  - Podpora jazyka R
  - Podpora modulu runtime pro vývojové nástroje R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (plně kompatibilní a uživatelsky kompatibilní překladač R s knihovnami škálování pro rychlejší výpočty na jednom uzlu nebo clusterech. Můžete také použít libovolný jazyk R z [Cran](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integrace SQL Serveru

::: moniker range="vs-2017"
SQL Server podporuje použití Pythonu i R k provádění pokročilých analýz přímo v SQL Server. Podpora jazyka R je součástí SQL Server 2016 a novějších verzí. Podpora Pythonu je k dispozici ve verzi SQL Server 2017 CTP 2,0 a novější.
::: moniker-end

::: moniker range=">=vs-2019"
SQL Server podporuje použití Pythonu k provádění pokročilých analýz přímo v SQL Server. Podpora Pythonu je k dispozici ve verzi SQL Server 2017 CTP 2,0 a novější.
::: moniker-end

Pomocí kódu, ve kterém vaše data už žijí, můžete využívat následující výhody:

- **Eliminace přesunu dat**: místo přesunu dat z databáze do aplikace nebo modelu můžete v databázi vytvářet aplikace. Tato funkce eliminuje překážky proti překážkám zabezpečení, dodržování předpisů, zásad správného řízení, integrity a hostiteli podobných problémů souvisejících s přesunem obrovského množství dat. Můžete také využívat datové sady, které se nedají umístit do paměti klientského počítače.

- **Snadné nasazení**: když máte model připravený, nasadíte ho do produkčního prostředí, je jednoduché ho vložit do skriptu T-SQL. Každá klientská aplikace SQL napsaná v jakémkoli jazyce pak může využít výhod modelů a inteligentního volání uložené procedury. Nejsou nutné žádné konkrétní jazykové integrace.

- **Výkon a škálování na podnikové úrovni**: v balíčcích RevoScale můžete SQL Server použít pokročilé možnosti, jako jsou tabulky v paměti a indexy úložiště sloupců s vysokým výkonem. Vyloučení přesunu dat také znamená, že se vyhnete omezením paměti klienta při zvětšování dat nebo chcete zvýšit výkon aplikace.

- **Bohaté rozšíření**: můžete nainstalovat a spustit kterýkoli z nejnovějších balíčků open source v nástroji SQL Server k vytváření aplikací pro hloubkové učení a AI pro velké objemy dat v SQL Server. Instalace balíčku v SQL Server je stejně jednoduchá jako instalace balíčku do místního počítače.

- **Bezplatná dostupnost bez dalších**poplatků: jazykové integrace jsou k dispozici ve všech edicích SQL Server 2017 a novějších, včetně edice Express.

Pokud chcete plně využít výhod SQL Server integrace, pomocí instalačního programu sady Visual Studio nainstalujte úlohu **ukládání a zpracování dat** pomocí možnosti **nástroje SQL Server Data Tools** . Druhá možnost umožňuje technologii SQL IntelliSense, zvýrazňování syntaxe a nasazení.

![Zátěžové úložiště a zpracování dat](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Možnosti úlohy úložiště a zpracování dat](media/workload/data-storage-workload-options.png)

Další informace najdete tady:

::: moniker range="vs-2017"
- [Práce s SQL Server a R](../rtvs/integrating-sql-server-with-r.md)
- [Pokročilá analýza v databázi pomocí R v SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python v SQL Server 2017: vylepšené v databázovém strojovém učení (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Další služby a sady SDK

Kromě toho, co je přímo v úloze datové vědy a analytické aplikace, je užitečná taky služba Azure Notebooks a sada Azure SDK pro Python je užitečná i pro datové vědy.

Sada Azure SDK pro Python usnadňuje využívání a správu Microsoft Azurech služeb z aplikací běžících na systémech Windows, Mac a Linux. Další informace najdete v tématu [sada Azure SDK pro Python](/azure/python/).

Azure Notebooks (aktuálně ve verzi Preview) poskytuje bezplatný online přístup k poznámkovým blokům Jupyter, které běží v cloudu v Microsoft Azure. Služba obsahuje ukázkové poznámkové bloky v Pythonu, R a F #, které vám pomohou začít. Navštivte [Notebooks.Azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Snímky obrazovky Azure Notebooks s ukázkou Úvod do jazyka R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
