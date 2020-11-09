---
title: Přístup k místním & vzdáleným datům (ClickOnce Apps)
description: Seznamte se s různými možnostmi, které ClickOnce poskytuje pro čtení a zápis dat, a to jak místně, tak i vzdáleně.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- data access, ClickOnce applications
ms.assetid: be5cbe12-6cb6-49c9-aa59-a1624e1eef3d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da8eaa4405a83ff349fd3d7486909a9281962126
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383258"
---
# <a name="access-local-and-remote-data-in-clickonce-applications"></a>Přístup k místním a vzdáleným datům v aplikacích ClickOnce
Většina aplikací spotřebovává nebo vytváří data. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nabízí celou řadu možností pro čtení a zápis dat, a to jak místně, tak i vzdáleně.

## <a name="local-data"></a>Místní data
 Pomocí [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nástroje můžete data načíst a uložit místně pomocí kterékoli z následujících metod:

- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Datový adresář

- Izolované úložiště

- Další místní soubory

### <a name="clickonce-data-directory"></a>Datový adresář ClickOnce
 Každá [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nainstalovaná v místním počítači má datový adresář uložený ve složce Documents and Settings uživatele. Všechny soubory zahrnuté v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci a označené jako "datový" se zkopírují do tohoto adresáře, když je aplikace nainstalovaná. Datové soubory můžou být libovolného typu souboru, nejčastěji používaný text, XML a databázové soubory, jako jsou soubory Microsoft Access. mdb.

 Datový adresář je určený pro data spravovaná aplikací, což jsou data, která aplikace explicitně ukládá a udržuje. Všechny statické, nezávislé soubory, které nejsou označeny jako "data" v manifestu aplikace, se místo toho nacházejí v adresáři aplikace. Do tohoto adresáře se nacházejí spustitelné soubory aplikace ( *. exe* ) a sestavení.

> [!NOTE]
> Při [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] odinstalaci aplikace je také odebrána její datový adresář. Nikdy nepoužívejte datový adresář k ukládání dat spravovaných koncovými uživateli, například dokumentů.

#### <a name="mark-data-files-in-a-clickonce-distribution"></a>Označení datových souborů v distribuci ClickOnce
 Chcete-li vložit existující soubor do datového adresáře, je nutné označit existující soubor jako datový soubor v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] souboru manifestu aplikace aplikace. Další informace naleznete v tématu [How to: include a data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

#### <a name="read-from-and-write-to-the-data-directory"></a>Čtení z datového adresáře a zápis do něj
 Čtení z datového adresáře vyžaduje, aby vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace vyžadovala oprávnění ke čtení. Podobně zápis do adresáře vyžaduje oprávnění k zápisu. Vaše aplikace bude mít toto oprávnění automaticky, pokud je nakonfigurována pro spuštění s úplným vztahem důvěryhodnosti. Další informace o oprávněních ke zvýšení oprávnění pro vaši aplikaci pomocí zvýšení oprávnění nebo nasazení důvěryhodné aplikace najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Pokud vaše organizace nepoužívá nasazení důvěryhodné aplikace a vypnula zvýšení oprávnění, neproběhne vyhodnocení oprávnění.

 Po tom, co vaše aplikace má tato oprávnění, může získat přístup k datovému adresáři pomocí volání metody třídy v rámci <xref:System.IO> . Cestu k datovému adresáři v aplikaci model Windows Forms můžete získat [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pomocí <xref:System.Deployment.Application.ApplicationDeployment.DataDirectory%2A> vlastnosti definované u <xref:System.Deployment.Application.ApplicationDeployment.CurrentDeployment%2A> vlastnosti <xref:System.Deployment.Application.ApplicationDeployment> . Toto je nejpohodlnější a doporučený způsob, jak získat přístup k datům. Následující příklad kódu ukazuje, jak to provést pro textový soubor s názvem *CSV.txt* , který jste zahrnuli do nasazení jako datový soubor.

 [!code-csharp[ClickOnce.OpenDataFile#1](../deployment/codesnippet/CSharp/accessing-local-and-remote-data-in-clickonce-applications_1.cs)]
 [!code-vb[ClickOnce.OpenDataFile#1](../deployment/codesnippet/VisualBasic/accessing-local-and-remote-data-in-clickonce-applications_1.vb)]

 Další informace o označování souborů v nasazení jako datových souborů naleznete v tématu [How to: include a data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).

 Můžete také získat cestu k datovému adresáři pomocí příslušných proměnných třídy, jako je například <xref:System.Windows.Forms.Application> <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A> .

 Manipulace s dalšími typy souborů může vyžadovat další oprávnění. Například pokud chcete použít soubor databáze aplikace Access ( *. mdb* ), aplikace musí uplatnit úplný vztah důvěryhodnosti, aby bylo možné použít příslušné \<xref:System.Data> třídy.

#### <a name="data-directory-and-application-versions"></a>Datové adresáře a verze aplikací
 Každá verze aplikace má svůj vlastní adresář dat, který je izolovaný od ostatních verzí. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Vytvoří tento adresář bez ohledu na to, jestli jsou nějaké datové soubory zahrnuté do nasazení, aby aplikace měla místo pro vytváření nových datových souborů za běhu. Pokud je nainstalována nová verze aplikace, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Nástroj zkopíruje všechny existující datové soubory z datového adresáře předchozí verze do datového adresáře nové verze – bez ohledu na to, zda byly zahrnuty do původního nasazení nebo vytvořeného aplikací.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nahradí starší verzi souboru novější verzí serveru, pokud má datový soubor jinou hodnotu hash ve staré verzi aplikace jako v nové verzi. V případě, že starší verze aplikace vytvořila nový soubor, který má stejný název jako soubor zahrnutý v nasazení nové verze, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] přepíše soubor staré verze novým souborem. V obou případech budou staré soubory zahrnuté v podadresáři v adresáři dat s názvem `.pre` , takže aplikace bude mít stále přístup k původním datům pro účely migrace.

 Pokud potřebujete jemnější migraci dat, můžete použít [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] rozhraní API nasazení k provedení vlastní migrace ze starého datového adresáře do nového adresáře dat. Budete muset otestovat dostupné stažení pomocí nástroje <xref:System.Deployment.Application.ApplicationDeployment.IsFirstRun%2A> , stáhnout aktualizaci pomocí nástroje <xref:System.Deployment.Application.ApplicationDeployment.Update%2A> nebo <xref:System.Deployment.Application.ApplicationDeployment.UpdateAsync%2A> a po dokončení aktualizace provést jakoukoli vlastní migraci dat na vlastní práci.

### <a name="isolated-storage"></a>Izolované úložiště
 Izolované úložiště poskytuje rozhraní API pro vytváření souborů a přístup k nim pomocí jednoduchého rozhraní API. Skutečné umístění uložených souborů je pro vývojáře i uživatele skryté.

 Izolované úložiště funguje ve všech verzích .NET Framework. Izolované úložiště také funguje v částečně důvěryhodných aplikacích bez nutnosti dalších udělení oprávnění. Izolované úložiště byste měli použít, pokud vaše aplikace musí běžet v částečném vztahu důvěryhodnosti, ale musí uchovávat data specifická pro aplikaci.

 Další informace najdete v tématu [izolované úložiště](/dotnet/standard/io/isolated-storage).

### <a name="other-local-files"></a>Další místní soubory
 Pokud vaše aplikace musí pracovat s daty koncových uživatelů, jako jsou například sestavy, obrázky, hudba a tak dále, aplikace bude vyžadovat <xref:System.Security.Permissions.FileIOPermission> čtení a zápis dat do místního systému souborů.

## <a name="remote-data"></a>Vzdálená data
 V určitém okamžiku bude vaše aplikace pravděpodobně muset načítat informace ze vzdáleného webu, jako jsou zákaznická data nebo informace o trhu. Tato část popisuje nejběžnější techniky načítání vzdálených dat.

### <a name="access-files-with-http"></a>Přístup k souborům pomocí protokolu HTTP
 K datům z webového serveru můžete přistupovat buď pomocí <xref:System.Net.WebClient> třídy, nebo <xref:System.Net.HttpWebRequest> třídy v <xref:System.Net> oboru názvů. Data mohou být buď statické soubory, nebo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikace, které vracejí nezpracovaný text nebo data XML. Pokud jsou vaše data ve formátu XML, nejrychlejší způsob, jak načíst data, je použití <xref:System.Xml.XmlDocument> třídy, jejíž <xref:System.Xml.XmlDocument.Load%2A> Metoda přijímá jako argument adresu URL. Příklad naleznete v tématu [čtení dokumentu XML do modelu DOM](/dotnet/standard/data/xml/reading-an-xml-document-into-the-dom).

 Pokud vaše aplikace přistupuje ke vzdáleným datům přes HTTP, musíte zvážit zabezpečení. Ve výchozím nastavení [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] může být přístup k síťovým prostředkům aplikace omezený v závislosti na tom, jak byla aplikace nasazena. Tato omezení platí pro zabránění škodlivým programům v získání přístupu k privilegovaným vzdáleným datům nebo k útoku na jiné počítače v síti pomocí počítače uživatele.

 Následující tabulka uvádí strategie nasazení, které můžete použít, a jejich výchozí webová oprávnění.

|Typ nasazení|Výchozí síťová oprávnění|
|---------------------|---------------------------------|
|Instalace na webu|Může přistupovat jenom k webovému serveru, ze kterého se aplikace nainstalovala.|
|Instalace sdílené složky|Nelze získat přístup k žádnému webovému serveru|
|Instalace CD-ROM|Má přístup k libovolným webovým serverům|

 Pokud vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nemůže získat přístup k webovému serveru z důvodu omezení zabezpečení, aplikace musí pro tento web vyhodnotit <xref:System.Net.WebPermission> . Další informace o zvýšení oprávnění zabezpečení pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md).

### <a name="access-data-through-an-xml-web-service"></a>Přístup k datům prostřednictvím webové služby XML
 Pokud vystavíte vaše data jako webovou službu XML, můžete k datům přistupovat pomocí proxy webové služby XML. Proxy je .NET Framework třída, kterou vytvoříte pomocí obou [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Operace webové služby XML, jako je například načítání zákazníků, umisťování objednávek atd., jsou zveřejněny jako metody na proxy serveru. Díky tomu je používání webových služeb mnohem snazší než nezpracovaný text nebo soubory XML.

 Pokud vaše webová služba XML funguje přes protokol HTTP, bude služba vázána stejnými omezeními zabezpečení jako <xref:System.Net.WebClient> třídy a <xref:System.Net.HttpWebRequest> .

### <a name="access-a-database-directly"></a>Přístup k databázi přímo
 Třídy v rámci oboru názvů můžete použít <xref:System.Data> k navázání přímých připojení s databázovým serverem, jako je například SQL Server ve vaší síti, ale je nutné, abyste měli účet pro problémy se zabezpečením. Na rozdíl od požadavků HTTP jsou požadavky na připojení k databázi ve výchozím nastavení vždycky zakázané, protože je částečně důvěryhodná; Toto oprávnění budete mít ve výchozím nastavení pouze v případě, že instalujete [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci z disku CD-ROM. Tím se vaše aplikace nastaví jako plně důvěryhodná. Aby bylo možné povolit přístup ke konkrétní databázi SQL Server, musí si ji aplikace požádat <xref:System.Data.SqlClient.SqlClientPermission> . Pokud chcete povolit přístup k jiné databázi než SQL Server, musí požádat o <xref:System.Data.OleDb.OleDbPermission> .

 Ve většině případů nebudete muset přistupovat k databázi přímo, ale místo toho se k ní přistupuje prostřednictvím aplikace webového serveru napsané v [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nebo v rámci webové služby XML. Přístup k databázi tímto způsobem je často nejlepší metodou, pokud je vaše [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace nasazena z webového serveru. K serveru můžete přistupovat v částečném vztahu důvěryhodnosti bez zvýšení oprávnění aplikace.

## <a name="see-also"></a>Viz také

- [Postupy: zahrnutí datového souboru do aplikace ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md)