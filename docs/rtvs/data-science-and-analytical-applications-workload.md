---
title: Úloha datové vědy a analytické aplikace
description: 'Úloha Thsi Visual Studio spojuje Python, R, F # a jejich odpovídajících runtime distribuce, včetně Anaconda.'
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 3d9815c72a500f9edd3b01f76dae3411ac0ee50f
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42624302"
---
# <a name="install-data-science-support-in-visual-studio"></a>Nainstalovat podporu datové vědy v sadě Visual Studio

Úlohy pro datové vědy a analytické aplikace, které výběru a instalaci pomocí instalačního programu sady Visual Studio, spojuje tři jazyky a jejich odpovídajících runtime distribuce:

- [R a Microsoft R Client](../rtvs/index.md)
- [Python a Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F # s použitím rozhraní .NET framework](/dotnet/fsharp/)

![Pro datové vědy a analytické aplikace funkcí v instalačním programu sady Visual Studio](media/data-science-workload.png)

R a Python jsou dvě primární skriptovací jazyky používané pro datové vědy. Oba jazyky se snadno učí a podporují bohatý ekosystém balíčků. Tyto balíčky adres širokou škálu scénářů, jako je získání dat, čištění, model školení, nasazení a vykreslení. F # je výkonná jazyková funkcionální .NET, která je vhodná pro širokou škálu úloh zpracování dat.

<!--Note link on the image because this one is large -->
[![Snímky obrazovky sady Visual Studio s R, Python nebo F #](media/data-science-workload-screens.png)](media/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Možnosti úlohy

Ve výchozím nastavení nainstaluje zatížení následující možnosti, které můžete upravit v části Souhrn pro zatížení v instalačním programu sady Visual Studio:

- Podpora jazyka F #
- Python:
  - Podpora jazyka Python
  - [Anaconda3, 64-bit](https://www.continuum.io) (A Python distribuce, která obsahuje knihovny rozsáhlé datové vědy a překladač Pythonu)
  - Podpora webů v Pythonu
  - Podpora šablon Cookiecutter
- R:
  - Podpora jazyka r.
  - Podpora modulu runtime pro vývojové nástroje R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (od Microsoftu plně kompatibilní, – podporované komunitou interpret R pomocí knihovny ScaleR pro rychlejší výpočty na jednotlivé uzly a clustery. Můžete také použít libovolný jazyka R z [CRAN](https://cran.r-project.org/).)

I když F # je součástí celou řadou dalších úloh a Python má zatížení vlastní, datové vědy a analytické aplikace je pouze úlohy v současné době, která zahrnuje R. Můžete ale také nainstalovat R nezávisle na zatížení. Na **jednotlivé komponenty** kartu v instalačním programu, vyberte následující možnosti R:

- **Vývojových aktivit** > **podpora jazyka r.**
- **Vývojových aktivit** > **Microsoft R Client**
- **Sestavení kompilátory, nástroje a moduly runtime** > **podpora modulu Runtime pro vývojové nástroje R**

## <a name="sql-server-integration"></a>Integrace SQL Serveru

Systém SQL Server podporuje pro pokročilé analýzy přímo v systému SQL Server pomocí R a Python. Podpora jazyka R je součástí systému SQL Server 2016 a vyšší. Podpora Pythonu je k dispozici v SQL serveru 2017 CTP 2.0 nebo novější.

Díky spouštění kódu, kde již vaše data kdekoli budete moct využívat následující výhody:

- **Odstranění přesun dat**: místo přesouvá data z databáze pro vaše aplikace nebo modelu, můžete vytvářet aplikace R a Python v databázi. Tato funkce eliminuje bariéry zabezpečení, dodržování předpisů, zásad správného řízení, integritu a celou řadu podobné problémy související s obrovských objemů dat po přesunutí. Můžete také využívat datové sady, který nelze umístit do paměti klientského počítače.

- **Snadné nasazení**: Jakmile máte R nebo Python model připravený, jeho nasazení do produkčního prostředí je jednoduché vkládání ve skriptu T-SQL. Všechny SQL klientské aplikace napsané v libovolném jazyce pak můžete využít výhod modely a inteligence pomocí volání uložené procedury. Nevzniká žádný konkrétní integrace R nebo Python.

- **Výkon na podnikové úrovni a škálování**: pokročilé funkce serveru SQL Server můžete použít jako tabulka v paměti a ve sloupci ukládat v balíčcích RevoScaleR a RevoScalePy indexy s rozhraními API pro vysoce výkonné škálovatelné. Úplného oproštění od přesunu dat taky znamená, že vyhnout tak klienta omezení paměti, jak roste vaše data nebo chcete zvýšit výkon aplikace.

- **Bohatá rozšiřitelnost**: můžete nainstalovat a spustit některý z nejnovějších open source balíčky R nebo Python v SQL serveru k sestavení aplikace AI a hloubkového učení na velké objemy dat v systému SQL Server. Instalace balíčku v systému SQL Server je jednoduché, stačí instalaci balíčku na místním počítači.

- **Široký dostupnost bez dalších poplatků**: integrace R a Python jsou k dispozici ve všech edicích systému SQL Server 2017 a novějších, včetně Express edition. (Podpora jazyka R je k dispozici v SQL serveru 2016 a novějším.)

Plně využít integraci s SQL serverem, použijte k instalaci instalačního programu sady Visual Studio **ukládání a zpracování dat** úlohy **SQL Server Data Tools** možnost. Druhou možnost umožňuje SQL IntelliSense, zvýrazňování syntaxe a nasazení.

![Úloze ukládání a zpracování dat](media/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Úložiště dat a zpracování úloh možností](media/data-storage-workload-options.png)

Další informace:

- [Práce s využitím SQL serveru a jazyka R](integrating-sql-server-with-r.md)
- [V databázi pokročilé analýzy s jazykem R v SQL serveru 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
- [Python v sadě SQL Server 2017: rozšířené v databázi machine learning (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>Další služby a sady SDK

Kromě přímo Novinky v úloze datové vědy a analytické aplikace služby Azure poznámkových bloků a sady Azure SDK for Python jsou také užitečná pro datové vědy.

Sada Azure SDK pro Python umožňuje snadno využívat a spravovat služby Micorosft Azure z aplikací běžících ve Windows, Mac a Linux. Další informace najdete v tématu [sady Azure SDK pro Python](../python/azure-sdk-for-python.md)

Azure poznámkových bloků (aktuálně ve verzi preview) poskytuje Bezplatná online přístup k poznámkové bloky Jupyter, které běží v cloudu v Microsoft Azure. Služba obsahuje ukázkové poznámkové bloky v Pythonu, R a F # vám pomůžou začít. Visit[notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Snímky obrazovky z Azure poznámkové bloky s Úvod do ukázkové R](media/data-science-workload-notebooks.png)](media/data-science-workload-notebooks.png#lightbox)
