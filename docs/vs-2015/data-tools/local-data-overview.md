---
title: Přehled lokálních dat | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- SQL Server, local data
- SQL Express
- SQL Server Compact
- data access [Visual Studio], troubleshooting
- Access, .mdb files in Visual Studio
- data [Visual Studio], local
ms.assetid: d6afa5ac-2bb8-49f2-a50e-f71f611ed506
caps.latest.revision: 71
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 94b3f066a66a380875609b4f6485d56a19ebde3e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49885574"
---
# <a name="local-data-overview"></a>Přehled lokálních dat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při vývoji datových aplikací, je obvykle vhodné použít místní kopii databáze, tak, aby nepoužijete chyby do produkční data. Potenciální problémy i sdílení s jinými vývojáři testovací databáze vytvoří, pokud dva vývojáři vzniku chyb, které interagovali obtížné rozpoznat. Všechny tyto nástrahy můžete vyhnout použitím zkušebních dat v místním počítači. Většina všechny databáze systémů umožňují vytvořit místní datové soubory. Pro projekty .NET Visual Studio poskytuje zvláštní podporu pro místní soubory databáze systému SQL Server (MDF) a soubory databáze Microsoft Access (MDB).  
  
 Visual Studio podporuje tyto scénáře:  
  
1.  
  
2.  
  
- 
  
- 
  
- Vytvořte projekt databáze SQL serveru tak, že kliknete na uzel řešení v Průzkumníku řešení a zvolíte **přidat &#124; nový projekt**.  V levém podokně vyberte **systému SQL Server &#124; databáze** projektu a klikněte na tlačítko OK. V Průzkumníku řešení klikněte pravým tlačítkem na uzel projektu databáze pro import souboru místní databáze a vyvíjet aplikace, která se připojuje k databázi vytvořené v projektu. Vhodné při vývoji a upravit schéma databáze ve stejnou dobu, kterou vyvíjíte aplikaci.  
  
   ![Import databáze do projektu databáze](../data-tools/media/raddata-import-database-into-database-project.png "raddata importovat databázi do projektu databáze")  
  
- Pokud vytváříte novou databázi, nejprve přidat **soubor databáze založené na službě** do vašeho projektu (**projektu &#124; přidat novou položku)**. Tím se vytvoří nový soubor MDF, který je připojen k výchozí instanci systému SQL Server na místním počítači, který ve výchozím nastavení je \MSSQLocalDB (localdb). Databáze by se zobrazit v Průzkumníku serveru. Rozbalte uzel a klikněte pravým tlačítkem na uzly pro přidání nové databázové objekty, jako například tabulky, zobrazení, funkce a tak dále.  
  
  Další informace o SQL serveru Express LocalDB, naleznete v tématu [představení LocalDB, vylepšení SQL Express](http://go.microsoft.com/fwlink/?LinkId=234375) a [LocalDB: kde je Moje databáze?](http://go.microsoft.com/fwlink/?LinkId=234376) na webu společnosti Microsoft.  
  
  Následující tabulka obsahuje odkazy na témata, která popisují, jak připojit aplikace k místním datům:  
  
|Téma|Popis|  
|-----------|-----------------|  
|[Vytvoření databáze SQL pomocí návrháře](../data-tools/create-a-sql-database-by-using-a-designer.md)|Poskytuje podrobné pokyny pro vytvoření místního databázového souboru, který slouží k testování funkcí dat a vytvářet aplikace.|  
|[Návod: Připojování k datům v lokálního databázového souboru (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)|Poskytuje podrobné pokyny pro připojení k databázi SQL Server Express LocalDB při vytvoření jednoduché aplikace Windows.|  
|[Připojení k datům v databázi Accessu (model Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)|Obsahuje podrobné pokyny pro připojení k databázi aplikace Microsoft Access.|  
|[Postupy: připojení k databázi Northwind](../data-tools/how-to-connect-to-the-northwind-database.md)|Obsahuje informace o připojení k ukázkové databázi Northwind v [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], SQL Server Compact, SQL Server Express a přístupu.|  
  
## <a name="use-the-connection-string"></a>Použijte připojovací řetězec  
 Toto je nejjednodušší přístup a je dobrou volbou, když aplikace čte pouze z databáze a při použití databází výrobců. Soubor databáze může být umístěna kdekoli na místním počítači, který má oprávnění pro přístup k aplikaci a že databázový systém podporuje.  
  
1.  (Volitelné) Vytvořit nové připojení, jak je popsáno v [přidat nové připojení](../data-tools/add-new-connections.md). Pro databází výrobců a soubory .mdf, u kterých již znáte připojovací řetězec a nebude se to vázání dat nebo využití zdroje dat, jako jsou třídy Entity Frameworku nebo datové sady tento krok není nezbytný. Použijte pouze připojovací řetězec pro připojení k místnímu souboru. Soubory .mdf, naleznete v tématu [Upgrade souborů .mdf](../data-tools/upgrade-dot-mdf-files.md) a [navazování připojení](https://msdn.microsoft.com/en-us/library/ms254507.aspx).  
  
2.  (Volitelné) Pokud používáte datové sady, Entity Framework a LINQ to SQL, vytvořte zdroj dat pomocí Průvodce konfigurací zdroje dat. Další informace najdete v tématu [přidat nové zdroje dat](../data-tools/add-new-data-sources.md).  
  
## <a name="add-an-existing-mdf-to-your-project"></a>Do projektu přidejte existující .mdf  
 Pokud vaše aplikace bude vkládání, odstraňování nebo aktualizace dat a chcete zachovat kopii původního souboru, který je k dispozici, zvažte přidání souboru do projektu. Když to uděláte, můžete nastavit vlastnost položky na něm k **kopírovat do výstupního adresáře** k **vždy Kopírovat** nebo **kopírovat, pokud je novější**a vyvíjet aplikace. Pokaždé, když vytvoříte aplikaci, je původní databáze je zkopírován do výstupní složky a jsou prováděny změny vašich aplikací na kopii. Díky tomu budete mít vždy kopii původní data vyčistit.  
  
1.  Použití **Průzkumníka souborů Windows** pro přetažení souboru .mdf z aktuálního umístění na uzel projektu v Průzkumníku řešení v sadě Visual Studio.  Pokud soubor je již připojen k instanci localDB, musíte ho nejprve odpojit. Po přemístění do projektu, Visual Studio se automaticky znovu připojí ho k výchozí instanci localDB.  
  
2.  Klikněte pravým tlačítkem na nový uzel databáze a zvolte možnost Vlastnosti. Buď vyberte chování kopírování **vždy Kopírovat** nebo **kopírovat, pokud je novější**.  
  
## <a name="create-a-sql-server-database-project-and-import-your-database"></a>Vytvořte projekt databáze SQL serveru a importujte databázi  
 Toto je vhodné při vám bude vyvíjet databáze, například přidání sloupců nebo tabulek, nebo změna datových typů.  
  
## <a name="each-project-contains-two-copies-of-the-database"></a>Každý projekt obsahuje dvě kopie databáze  
 Při vytváření projektu může být zkopírovat databázový soubor z kořenové složky projektu do výstupní **bin**, složku. Toto chování závisí **kopírovat do výstupního adresáře** vlastnosti souboru a výchozí hodnota této vlastnosti závisí na typu databázového souboru, který používáte.  
  
 Chcete-li zobrazit **bin** složky **Průzkumníku řešení**, zvolte **zobrazit všechny soubory** tlačítko na panelu nástrojů.  
  
> [!NOTE]
>  **Kopírovat do výstupního adresáře** vlastnost se nevztahuje na web nebo projekty C++.  
  
 Soubor databáze v kořenové složce projektu se změní pouze při úpravách schématu databáze nebo data s využitím **Průzkumníka serveru**/**Průzkumník databáze** nebo jiné [Visual Databázové nástroje](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Při změně dat během vývoje aplikace měníte databázi **bin** složky. Například pokud zvolíte klávesu F5 pro ladění vaší aplikace, budete připojeni k databázi v dané složce.  
  
|Hodnota **kopírovat do výstupního adresáře** vlastnost|Chování|  
|----------------------------------------------------|--------------|  
|**Kopírovat, pokud je novější** (výchozí hodnota pro soubory SDF)|Databázový soubor je zkopírován z adresáře projektu do **bin** adresáře při prvním sestavení projektu. **Datum změny** vlastnost souborů se následně porovnává pokaždé při sestavení projektu. Pokud soubor ve složce projektu je novější, je zkopírován do **bin** složky, nahradí předcházející soubor. V opačném případě nejsou zkopírovány žádné soubory. **Upozornění:** nedoporučujeme tuto hodnotu pro soubory .mdb nebo mdf. Soubor databáze se může změnit i v případě, že se data nemění. Soubor může být označen jako novější, pokud jednoduše otevřete připojení (například rozšířit **tabulky** uzel v **Průzkumníka serveru**).|  
|**Vždy kopírovat** (výchozí hodnota pro soubory MDF a MDB)|Databázový soubor je zkopírován z adresáře projektu do **bin** directory pokaždé, když vytváříte aplikaci. Všechny změny provedené v souboru dat ve výstupní složce jsou přepsány při příštím spuštění aplikace.|  
|**Nekopírovat**|Systém nikdy přepíše soubor v **bin** adresáře. Aplikace vytvoří dynamický připojovací řetězec, který odkazuje na databázový soubor ve výstupním adresáři. Proto je musíte ručně zkopírovat soubor do výstupního adresáře. Pokud chcete data ve výstupním adresáři odpovídala datům v adresáři projektu.|  
  
## <a name="common-issues-with-local-data"></a>Běžné problémy s místními daty  
 Následující tabulka popisuje běžné problémy, které můžete narazit při práci s místní datové soubory.  
  
|Problém|Vysvětlení|  
|-----------|-----------------|  
|Pokaždé, když mám aplikaci a Měním data, jsou změny při příštím spuštění aplikace pryč.|Hodnota **kopírovat do výstupního adresáře** vlastnost **kopírovat, pokud je novější** nebo **vždy Kopírovat**. Databáze ve výstupní složce (databáze, která je právě upravována při testování aplikace) je přepsána pokaždé, když svůj projekt sestavit. Další informace najdete v tématu [jak: Manage Local Data Files in Your Project](../data-tools/how-to-manage-local-data-files-in-your-project.md).|  
|Zobrazí se zpráva s informacemi o tom, že datový soubor je uzamčen.|Access (soubory MDB): Ověřte, že soubor není otevřen v jiném programu, jako je například přístup.<br /><br /> SQL Server Express (soubory MDF): SQL Express uzamkne soubor dat, pokud se pokusíte zkopírovat, přesunout nebo přejmenovat mimo rozhraní IDE sady Visual Studio.|  
|Přístup byl odepřen, pokud více než jeden uživatel pokusí o přístup k databázi stejné ve stejnou dobu.|Visual Studio využívá výhod *uživatelské instance*, což je funkce systému SQL Server Express, která vytváří samostatnou instanci systému SQL Server pro každého uživatele. Jakmile jeden uživatel přistoupí k souboru, žádný další uživatel se nemůže připojit. Tomuto problému může dojít, pokud se například pokusíte spustit webovou aplikaci v ASP.NET Development Server a Internetové informační služby (IIS) ve stejnou dobu, protože služba IIS obvykle pracuje pod jiným účtem.|  
  
## <a name="see-also"></a>Viz také  
 [Návod: Připojování k datům v lokálního databázového souboru (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Připojení k datům v databázi Accessu (model Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)