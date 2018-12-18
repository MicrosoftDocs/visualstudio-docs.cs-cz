---
title: Řešení potíží s poškozenými odkazy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
ms.assetid: 00a9ade9-652e-40de-8ada-85f63cd183ee
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae619be498fcb1c48bbea8b706f0b0b5fa4db54c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950664"
---
# <a name="troubleshooting-broken-references"></a>Řešení potíží s poškozenými odkazy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud vaše aplikace se pokusí použít poškozený odkaz, je vygenerována chyba výjimky. Nebylo možné najít odkazovaná součást je primární aktivační událost pro chybu, ale existuje několik situací ve kterých lze považovat za odkazem nefunkční. Tyto instance jsou uvedeny v následujícím seznamu:  
  
- Cesta odkazu projekt je nesprávné nebo neúplné.  
  
- Odkazovaný soubor se odstranil.  
  
- Odkazovaný soubor byl přejmenován.  
  
- Připojení k síti nebo ověřování se nezdařilo.  
  
- Odkazuje na komponentu modelu COM, který není nainstalován v počítači.  
  
  Toto jsou řešení těchto problémů.  
  
> [!NOTE]
>  Soubory v sestavení je odkazováno pomocí absolutní cesty v souboru projektu. Proto je možné pro uživatele, kteří pracují v prostředí vývoj chybí odkazovaná sestavení svého místního prostředí. Aby nedocházelo k těmto chybám, je lepší v těchto případech pro přidání odkazů typu projekt projekt. Další informace najdete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) a [programování se sestaveními](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6).  
  
## <a name="reference-path-is-incorrect"></a>Cesta odkazu je nesprávný  
 Pokud projekty jsou sdíleny v různých počítačích, nemusí při komponenty se nachází v jiném adresáři na každém počítači nalezeny některé odkazy. Odkazy jsou uloženy pod názvem souboru součásti (například MyComponent). Při přidání odkazu do projektu, umístění složky souboru součásti (například C:\MyComponents\\) se připojí **ReferencePath** vlastnosti projektu.  
  
 Při otevření projektu, pokusy o vyhledání těchto souborů odkazovaná součást vyhledáváním v adresářích na zadané cestě odkazu. Pokud je projekt otevřít v počítači, který ukládá komponenty v jiném adresáři, jako je například D:\MyComponents\\, se nenašel odkaz a chyba se zobrazí v seznamu úkolů.  
  
 Chcete-li vyřešit tento problém, můžete odstranit poškozený odkaz a nahradili ho pomocí dialogového okna Přidat odkaz. Druhým řešením je použít **cestu odkazu** položek na stránkách vlastností projektu a upravit složky v seznamu tak, aby odkazovala na správné umístění. **Cestu odkazu** trvale uloženou vlastnost pro každého uživatele na každém počítači. Změna cesty k odkazu proto neovlivňuje ostatní uživatelé z projektu.  
  
> [!TIP]
>  Odkazy typu projekt projekt není nutné tyto problémy. Z tohoto důvodu je použijte místo odkazy na soubory, pokud je to možné.  
  
#### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>Chcete-li vyřešit poškozený odkaz projektu tím, že opraví cesta odkazu  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel projektu a klikněte na tlačítko **vlastnosti**.  
  
2.  **Návrháře projektu** se zobrazí.  
  
3.  Pokud používáte Visual Basic, vyberte **odkazy** stránky a klikněte na tlačítko **cesty odkazů** tlačítko. V **cesty odkazů** dialogového okna zadejte cestu ke složce, která obsahuje položku, kterou chcete odkazovat **složky** pole a potom klikněte na **přidat složku** tlačítko.  
  
     -nebo-  
  
     Pokud používáte jazyk Visual C#, vyberte **cesty odkazů** stránky. V **složky** pole, zadejte cestu ke složce, která obsahuje položku, kterou chcete odkazovat a klikněte **přidat složku** tlačítko.  
  
## <a name="referenced-file-has-been-deleted"></a>Odkazovaný soubor byl odstraněn.  
 Je možné, že odkazovaný soubor je odstraněný a už neexistuje na disku.  
  
#### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>Chcete-li vyřešit porušení projektu odkaz pro soubor, který již existuje na disku  
  
-   Odstraňte odkaz.  
  
-   Pokud existuje odkaz na jiné místo v počítači, přečtěte si je z tohoto umístění.  
  
-   Další informace najdete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="referenced-file-has-been-renamed"></a>Odkazovaný soubor byl přejmenován.  
 Je možné, že byl přejmenován soubor, který se odkazuje.  
  
#### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>Chcete-li vyřešit poškozený odkaz pro soubor, který se přejmenoval  
  
-   Odstranit odkazy a pak přidejte odkaz na soubor přejmenován.  
  
-   Pokud existuje odkaz na jiné místo v počítači, je nutné jej načíst z tohoto umístění. Další informace najdete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="network-connection-or-authentication-has-failed"></a>Připojení k síti nebo ověřování se nezdařilo  
 Může být mnoho možných příčin nepřístupných souborů: došlo k chybě síťového připojení nebo se nezdařilo ověřování, například. Každou příčinou může být jedinečný prostředek obnovení; například budete muset obrátit na místního správce pro přístup k potřebným prostředkům. Odstranění odkazu a oprava kódu, který používá ho ale vždy možnost. Další informace najdete v tématu [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
## <a name="com-component-is-not-installed-on-computer"></a>V počítači není nainstalována komponenta modelu COM  
 Pokud uživatel byl přidán odkaz na komponentu COM a druhý uživatel pokusí o spuštění kódu na počítači, který nemá tuto součást nainstalovaná, druhý uživatel dojde k chybě, že je odkaz poškozený. Instalace součásti na druhý počítač bude opravte chybu. Další informace o tom, jak pomocí odkazů na komponenty modelu COM ve vašich projektech najdete v tématu [interoperabilita modelů COM v aplikacích .NET Framework](http://msdn.microsoft.com/library/f5a72143-c268-4dff-a019-974ad940e17d).  
  
## <a name="see-also"></a>Viz také  
 [Úvod do Návrháře projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [Stránka odkazy, Návrhář projektu (Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)   
 [NIB postupy: Přidání nebo odebrání odkazů pomocí dialogového okna Přidat odkaz](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)



