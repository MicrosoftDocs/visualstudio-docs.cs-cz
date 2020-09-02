---
title: Stránka publikování, Návrhář projektu (vývoj pro Office)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86d575b254209b547504ea6d746d03853990bfb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "67328999"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Stránka publikování, Návrhář projektu (vývoj pro Office v sadě Visual Studio)
  Stránka **publikovat** v **Návrháři projektu** se používá ke konfiguraci vlastností pro nasazení.

 Chcete-li získat přístup k této stránce, vyberte projekt v **Průzkumník řešení**a potom v nabídce **projekt** zvolte vlastnosti *ProjectName* **Properties**. Pokud se stránka **publikování** nezobrazí, klikněte na kartu **publikovat** .

> [!NOTE]
> Umístění pro publikování můžete také nastavit v **Průvodci publikováním**. Další informace naleznete v tématu [How to: Publishing a řešení Office using ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).

## <a name="uielement-list"></a>UIElement – seznam
 **Umístění složky pro publikování (web, server FTP nebo cesta k souboru)** Požadovanou.

 Umístění složky pro publikování je adresář, do kterého aplikace Visual Studio kopíruje soubory řešení, například manifesty, sestavení a další soubory ze sestavení. Musíte mít přístup pro zápis do tohoto adresáře.

 Mezi možnosti patří místní počítač, sdílená složka UNC nebo webová stránka HTTP/HTTPS. Cesta může být místní (*c:\FolderName\PublishFolder*), relativní (* \\ publikovat*) nebo plně kvalifikované umístění (* \\ \servername\foldername* nebo http://<em>servername/název_složky</em>).

 Ve výchozím nastavení je umístění publikování v *http://localhost/projectname/* případě, že máte nainstalovanou službu IIS, nebo pokud adresář pro *publikování \\ * nemáte nainstalovanou službou IIS.

 **Adresa URL instalační složky** Volitelné.

 Adresa URL instalační složky je adresář, ze kterého bude koncový uživatel instalovat vlastní nastavení. Je to také cesta, kterou řešení použije ke kontrole aktualizací. Cesta může být stejná jako umístění složky pro publikování, ale nejedná se o požadavek.

 Mezi možnosti patří místní počítač, sdílená složka UNC nebo webová stránka HTTP/HTTPS. Cesta může být místní (*c:\FolderName\PublishFolder*), relativní (* \\ publikovat*) nebo plně kvalifikované umístění (* \\ \servername\foldername* nebo http://<em>servername/název_složky</em>). Všechna umístění HTTP/HTTPS musí být vytvořená pomocí znaků US-ASCII. Znaky Unicode nejsou podporovány.

 Pokud je nastavená cesta instalace, musí být soubory vlastního nastavení v tomto umístění, aby si uživatelé mohli vlastní nastavení nainstalovat. Umístění by mělo být nastaveno pouze v případě, že znáte konečné umístění nasazení.

 Pokud jsou instalační soubory v umístění relativním k dokumentu nebo instalačnímu programu, například s možností CD, ponechte toto pole prázdné.

 Tuto hodnotu může přiřadit správce později. Další informace najdete v tématu [Postup: změna instalační cesty řešení Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 **Požadavky** Požadavky mohou být součástí instalačního programu nebo staženy na vyžádání během instalace.

- **Stáhnout požadavky z webu dodavatele součásti**: tuto možnost použijte, chcete-li stáhnout tyto požadavky od společnosti Microsoft.

- **Stáhnout požadavky ze stejného umístění jako moje aplikace**: tuto možnost použijte, pokud chcete zabalit požadavky v instalačním programu. Zahrnutí souborů požadovaných součástí s instalačním programem zvyšuje velikost řešení.

- **Stáhnout požadavky z následujícího umístění**: tuto možnost použijte, pokud chcete, aby byly požadavky k dispozici koncovým uživatelům samostatně jako jiný instalační program na webové stránce nebo ve sdílené síťové složce.

  **Aktualizace** Interval aktualizace určuje, jak často řešení kontroluje aktualizace. Ve výchozím nastavení se bude kontrolovat každých 7 dní.

  Vyhledávání aktualizací pokaždé, když se načte přizpůsobení na úrovni dokumentu nebo doplněk VSTO, by se zachovala aktualizace, ale má vliv na výkon při spuštění.

  Pokud nasazujete pomocí disku CD nebo vyměnitelné jednotky, nastavte tuto hodnotu na Nevyhledávat **aktualizace**.

  **Možnosti (Description)** Můžete nastavit možnosti publikování pro následující vlastnosti:

- Jazyk publikování: národní prostředí řešení pro Office.

- Název vydavatele: název společnosti nebo vývojáře, jak se zobrazuje v části **Přidat nebo odebrat programy** nebo **programy a funkce**.

- Název produktu: název řešení pro Office, jak se zobrazuje v části **Přidat nebo odebrat programy** nebo **programy a funkce**.

- Adresa URL podpory: umístění koncových uživatelů, kteří budou kontaktovat technickou podporu řešení pro Office.

  **Možnosti (nastavení Office)** Můžete nastavit možnosti publikování pro následující vlastnosti:

- Název řešení: název řešení pro Office, jak se zobrazuje v aplikaci Office.

- Popis: popis řešení Office, jak se zobrazuje v aplikaci Office.

- Chování při načítání doplňku VSTO.

  - Načíst při spuštění: Určuje, jestli se doplněk VSTO načte při spuštění aplikace Office.

  - Load on demand: Určuje, jestli se doplněk VSTO načte, když ho aplikace vyžaduje, třeba když uživatel klikne na prvek uživatelského rozhraní, který používá funkce v doplňku VSTO.

  **Jazyk publikování** Tato možnost nastaví jazyk licenčních podmínek pro software společnosti Microsoft a zahrne jazykové sady v seznamu požadavků. Nemá vliv na jazyk vlastního nastavení. Jazyk v instalačním programu je určen nainstalovanými jazyky sady Visual Studio.

  Další informace o tom, jak změnit **jazyk publikování**, naleznete v tématu [How to: Change the Publishing Language for a ClickOnce Application](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Verze publikování** Nastaví číslo verze pro vlastní nastavení. Když se změní číslo verze, aplikace se publikuje jako aktualizace. Vytvoří se nová složka pro každou verzi během procesu sestavení, aby se zabránilo přepsání dříve publikované verze. Každá část verze publikování (**Hlavní**, **podverze**, **sestavení**, **Revize**) může obsahovat až pět číslic.

  **Automaticky zvyšovat revize u každé vydané verze** Volitelné. Je-li tento příkaz vybrán (výchozí možnost), **je část čísla** verze zvětšena o jednu pokaždé, když je přizpůsobení Publikováno. Tím dojde k publikování vlastního nastavení jako aktualizace.

  **Publikovat hned** Publikuje aplikaci pomocí aktuálního nastavení. Ekvivalent tlačítka **Dokončit** v **Průvodci publikováním**.

## <a name="see-also"></a>Viz také

- [Nasazení řešení pro systém Office](../vsto/deploying-an-office-solution.md)
- [Nasazení řešení Office pomocí technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Požadavky na řešení systému Office pro nasazení](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
