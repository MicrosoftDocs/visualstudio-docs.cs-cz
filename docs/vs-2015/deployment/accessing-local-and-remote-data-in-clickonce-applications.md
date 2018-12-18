---
title: Přístup k lokálním a vzdáleným datům v aplikacích ClickOnce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4fe0c0b1cd7659a5887f267181ffd6fa7bb5e8d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218833"
---
# <a name="accessing-local-and-remote-data-in-clickonce-applications"></a>Přístup k lokálním a vzdáleným datům v aplikacích ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Většina aplikací spotřebovávají nebo vytvářejí data. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] poskytuje širokou škálu možností pro čtení a zápis dat, místně i vzdáleně.  
  
## <a name="local-data"></a>Místní Data  
 S [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], můžete načíst a ukládat data místně pomocí jedné z následujících metod:  
  
-   [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Datový adresář  
  
-   Izolované úložiště  
  
-   Další místní soubory  
  
### <a name="clickonce-data-directory"></a>Adresář dat ClickOnce  
 Každý [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace je nainstalovaná na místním počítači má datový adresář, který je uložený ve složce Dokumenty a nastavení uživatele. Všechny soubory součástí [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace a označena jako "data" soubor zkopírován do tohoto adresáře, když je nainstalovaná určitá aplikace. Datové soubory mohou být libovolného typu souboru, nejčastěji používané text, XML a soubory databáze, jako jsou například aplikace Microsoft Access .mdb soubory.  
  
 Do adresáře dat je určená pro data spravované aplikace, které jsou data, která aplikace explicitně uchovává a udržuje. Všechny statické, nezávislé soubory nejsou označeny jako "data" v manifestu aplikace se místo toho jsou umístěny v adresáři aplikace. Tento adresář je, kde jsou umístěné spustitelné soubory (.exe) a sestavení aplikace.  
  
> [!NOTE]
>  Když [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace se odinstaluje, odebere se také jeho Data adresáře. Nikdy nepoužívejte datový adresář k uložení dat spravované end uživatele, jako jsou například dokumenty.  
  
#### <a name="marking-data-files-in-a-clickonce-distribution"></a>Označení datové soubory v distribuci ClickOnce  
 Umístit existující soubor do adresáře dat, je třeba označit existující soubor jako datový soubor v vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] souboru manifestu aplikace vaší aplikace. Další informace najdete v tématu [postupy: zahrnutí datového souboru do aplikace ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
#### <a name="reading-from-and-writing-to-the-data-directory"></a>Čtení a zápis dat adresáře  
 Čtení z adresáře dat vyžaduje, aby vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] žádosti o oprávnění ke čtení; podobně zápisu do adresáře, vyžaduje oprávnění k zápisu. Vaše aplikace nebude mít toto oprávnění automaticky, pokud je nakonfigurován na spuštění s úplnou důvěryhodností. Další informace o zvyšování oprávnění pro vaši aplikaci pomocí rozhraní zvýšení úrovně oprávnění nebo Trusted Application Deployment najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).  
  
> [!NOTE]
>  Pokud vaše organizace nepoužívá Trusted Application Deployment a zvýšení oprávnění se vypnulo, uplatnění oprávnění se nezdaří.  
  
 Poté, co vaše aplikace má tato oprávnění, má přístup do adresáře dat pomocí volání metody třídy v rámci <xref:System.IO>. Můžete získat cestu do adresáře dat v rámci prvku Windows Forms [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace s použitím <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> vlastnosti definované v <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> vlastnost <xref:System.Deployment.Application.ApplicationDeployment>. Toto je nejpohodlnější a doporučený způsob pro přístup k datům. Následující příklad kódu ukazuje, jak to provést u textového souboru s názvem CSV.txt, kterou jste zadali ve vašem nasazení jako datový soubor.  
  
 [!code-csharp[ClickOnce.OpenDataFile#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.OpenDataFile/CS/Form1.cs#1)]
 [!code-vb[ClickOnce.OpenDataFile#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.OpenDataFile/VB/Form1.vb#1)]  
  
 Další informace o označení souborů ve vašem nasazení jako datové soubory, naleznete v tématu [postupy: zahrnutí datového souboru do aplikace ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
 Můžete také získat cestu k adresáři data pomocí příslušných proměnných na <xref:System.Windows.Forms.Application> třídy, jako například <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A>.  
  
 Manipulace s další typy souborů můžou vyžadovat další oprávnění. Například pokud chcete použít souboru databáze Access (MDB), aplikace musí uplatnit úplný vztah důvěryhodnosti pro použití příslušných <xref:System.Data> třídy.  
  
#### <a name="data-directory-and-application-versions"></a>Adresář data a verze aplikace  
 Každá verze aplikace má vlastní datový adresář, který je izolovaný od ostatních verzí. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] vytvoří tento adresář bez ohledu na to, zda jsou všechny datové soubory zahrnuté v nasazení tak, aby aplikace měla umístění pro vytvoření nové datové soubory v době běhu. Při instalaci nové verze aplikace [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zkopíruje všechny existující soubory dat z předchozí verze datový adresář do adresáře dat novou verzi – Určuje, zda byly zahrnuty do původního nasazení nebo vytvořené aplikace.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nahradí starší verzi souboru v novější verzi serveru datový soubor má jiný algoritmus hash hodnoty v původní verze aplikace jako novou verzi. Navíc pokud starší verzi aplikace vytvořila nový soubor, který má stejný název jako soubor součástí nasazení nové verze [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] stará verze souboru přepíše novým souborem. V obou případech se zahrne starých souborů v podadresáři do adresáře dat s názvem `.pre`, aby aplikace stále přístup k stará data pro účely migrace.  
  
 Pokud potřebujete citlivější migraci dat, můžete použít [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] rozhraní API nasazení provést vlastní migraci ze staré adresář dat do nového adresáře Data. Budete muset pomocí otestovat k dispozici ke stažení <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A>, stáhnout aktualizace pomocí <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> nebo <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A>, a provést vlastní migraci dat fungovat vlastní po instalaci aktualizace je dokončena.  
  
### <a name="isolated-storage"></a>Izolované úložiště  
 Izolované úložiště poskytuje rozhraní API pro vytváření a přístup k souborům s použitím jednoduchého rozhraní API. Skutečné umístění uložené soubory se skryje vývojáře a uživatele.  
  
 Izolované úložiště funguje ve všech verzích [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Izolované úložiště funguje taky v částečně důvěryhodné aplikace bez nutnosti udělení dalších oprávnění. Izolované úložiště byste měli použít, pokud vaše aplikace musí spustit v částečném vztahu důvěryhodnosti, ale musí spravovat data specifická pro aplikaci.  
  
 Další informace najdete v tématu [izolovaného úložiště](http://msdn.microsoft.com/library/aff939d7-9e49-46f2-a8cd-938d3020e94e).  
  
### <a name="other-local-files"></a>Další místní soubory  
 Pokud vaše aplikace musí fungovat s nebo uložit data koncových uživatelů, jako jsou sestavy, obrázky, Hudba a tak dále, aplikace bude vyžadovat <xref:System.Security.Permissions.FileIOPermission> ke čtení a zápis dat do místního systému souborů.  
  
## <a name="remote-data"></a>Vzdálená Data  
 V určitém okamžiku vaše aplikace bude mít pravděpodobně k načtení informací ze vzdáleného webu, jako je například informace o zákaznících dat nebo na trhu. Tato část popisuje nejběžnější techniky pro načítání vzdálených dat.  
  
### <a name="accessing-files-by-using-http"></a>Přístup k souborům pomocí protokolu HTTP  
 Můžete přístup k datům z webového serveru pomocí <xref:System.Net.WebClient> nebo <xref:System.Net.HttpWebRequest> třídy v <xref:System.Net> oboru názvů. Data mohou být buď statické soubory nebo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace, které vracejí nezpracovaný text nebo XML data. Pokud jsou vaše data ve formátu XML, je nejrychlejší způsob, jak načíst data pomocí <xref:System.Xml.XmlDocument> třídy, jejichž <xref:System.Xml.XmlDocument.Load%2A> metoda přebírá adresu URL jako argument. Příklad najdete v tématu [čtení dokumentu XML do modelu DOM](http://msdn.microsoft.com/library/a4fb291f-5630-49ba-a49a-5b66c3b71e49).  
  
 Je nutné zvážit zabezpečení, když vaše aplikace přistupuje vzdálených dat prostřednictvím protokolu HTTP. Ve výchozím nastavení vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace přístup k síťovým prostředkům může být omezená, v závislosti na tom, jak se vaše aplikace nasazena. Tato omezení se použijí na škodlivé programy zabránit v získání přístupu k privilegovaným vzdálených dat nebo z počítače uživatele pomocí k útoku na jiné počítače v síti.  
  
 Následující tabulka uvádí strategie nasazení, které můžete použít a jejich oprávnění výchozí Web.  
  
|Typ nasazení|Výchozí oprávnění sítě|  
|---------------------|---------------------------------|  
|Webová instalace|Můžete pouze přístup k webovému serveru, ze kterého byla aplikace nainstalována|  
|Instalace ze sdílené složky|Nelze získat přístup k webové servery|  
|Instalace CD-ROM|Můžete přistupovat na webové servery|  
  
 Pokud vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace nemůže přistupovat k webového serveru z důvodu omezení zabezpečení, musí aplikace uplatnit <xref:System.Net.WebPermission> pro tento web. Další informace o zvýšení oprávnění zabezpečení pro [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, najdete v článku [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).  
  
### <a name="accessing-data-through-an-xml-web-service"></a>Přístup k datům prostřednictvím webové služby XML  
 Pokud je zveřejnit vaše data jako webové služby XML, můžete přístup k datům pomocí proxy XML webové služby. Server proxy je [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] třídy můžete vytvořit buď pomocí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Operace webové služby XML, třeba načítání zákazníků, uvedení objednávky a tak dále – jsou vystaveny jako metody na proxy serveru. To umožňuje mnohem jednodušší než nezpracovaný text nebo soubory XML webové služby.  
  
 Pokud vaše webová služba XML pracuje přes protokol HTTP, služba bude vázána stejná omezení zabezpečení, jako <xref:System.Net.WebClient> a <xref:System.Net.HttpWebRequest> třídy.  
  
### <a name="accessing-a-database-directly"></a>Přístup k databázi  
 Můžete použít třídy v rámci <xref:System.Data> obor názvů a navázat přímé spojení s databázovým serverem, jako je SQL Server v síti, ale musí odpovídat problémy se zabezpečením. Na rozdíl od požadavků protokolu HTTP žádosti o připojení databáze jsou vždy je zakázané ve výchozím nastavení v částečném vztahu důvěryhodnosti; je jenom taková oprávnění budete mít ve výchozím nastavení při instalaci vašeho [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci z disku CD-ROM. Díky tomu vaše aplikace úplné důvěryhodnosti. Pokud chcete povolit přístup ke konkrétní databázi systému SQL Server, vaše aplikace musí požádat o <xref:System.Data.SqlClient.SqlClientPermission> k němu; zajistit přístup k jiné databáze než SQL Server, musíte požádat o <xref:System.Data.OleDb.OleDbPermission>.  
  
 Ve většině případů, nebudete mít přístup k databázi přímo, ale bude získávat přístup místo toho prostřednictvím serveru webové aplikace napsané v [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] nebo webové služby XML. Přístup k databázi tímto způsobem je často nejlepší metody Pokud vaše [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení aplikace z webového serveru. Přístup k serveru v částečném vztahu důvěryhodnosti bez zvýšené oprávnění vaší aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Zahrnutí datového souboru do aplikace ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)



