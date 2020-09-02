---
title: 'Postupy: načtení informací řetězce dotazu v online aplikaci ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 588ff95f90c6d85526dfe931e8f0b8ab439d9b94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697584"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Postupy: Načtení informací řetězce dotazu do online aplikace ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Řetězec dotazu* je část adresy URL začínající otazníkem (?), která obsahuje libovolné informace ve tvaru *název = hodnota*. Předpokládejme, že máte [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci s názvem `WindowsApp1` , na kterou jste hostitelem `servername` , a chcete předat hodnotu proměnné `username` při spuštění aplikace. Adresa URL může vypadat takto:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Následující dva postupy ukazují, jak použít [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci k získání informací o řetězci dotazu.  
  
> [!NOTE]
> Informace v řetězci dotazu můžete předávat jenom v případě, že se aplikace spouští pomocí protokolu HTTP namísto použití sdílené složky nebo místního systému souborů.  
  
 První postup ukazuje, jak [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] může vaše aplikace používat malou část kódu ke čtení těchto hodnot při spuštění aplikace.  
  
 Následující postup ukazuje, jak nakonfigurovat [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci pomocí MageUI.exe tak, aby mohla přijímat parametry řetězce dotazu. To je nutné provést při každém publikování aplikace.  
  
> [!NOTE]
> V části zabezpečení níže v tomto tématu se můžete rozhodnout, že tuto funkci povolíte.  
  
 Informace o tom, jak vytvořit [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nasazení pomocí Mage.exe nebo MageUI.exe, naleznete v tématu [Návod: Ruční nasazení aplikace ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
> Počínaje .NET Framework 3,5 SP1 je možné předat argumenty příkazového řádku do offline [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace. Chcete-li zadat argumenty do aplikace, můžete předat parametry do souboru zástupce pomocí. Rozšíření APPREF-MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Získání informací o řetězci dotazu z aplikace ClickOnce  
  
1. Do projektu vložte následující kód. Aby tento kód fungoval, bude nutné mít odkaz na System. Web a přidat `using` nebo `Imports` příkazy pro System. Web, System. Collections. Specialized a System. Deployment. Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnceQueryString/CS/Form1.cs#1)]
     [!code-vb[ClickOnceQueryString#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceQueryString/VB/Form1.vb#1)]  
  
2. Volejte dříve definovanou funkci pro načtení <xref:System.Collections.DictionaryBase.Dictionary%2A> parametrů řetězce dotazu indexovaného podle názvu.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Povolení předávání řetězců dotazů v aplikaci ClickOnce pomocí MageUI.exe  
  
1. Otevřete příkazový řádek .NET a zadejte:  
  
    ```  
    MageUI  
    ```  
  
2. V nabídce **soubor** vyberte možnost **otevřít**a otevřete manifest nasazení [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikace, což je soubor končící `.application` příponou.  
  
3. V levém navigačním okně vyberte panel **Možnosti nasazení** a zaškrtněte políčko **povoluje předání parametrů adresy URL do aplikace** .  
  
4. V nabídce **soubor** vyberte **Uložit**.  
  
> [!NOTE]
> Alternativně můžete povolit předávání řetězce dotazu v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . Zaškrtněte políčko **Allow URL Parameters Passed to Application** , které lze najít otevřením **vlastností projektu**, výběrem karty **publikovat** , kliknutím na tlačítko **Možnosti** a následným výběrem **Manifests**.  
  
## <a name="robust-programming"></a>Robustní programování  
 Při použití parametrů řetězce dotazu musíte pečlivě zvážit, jak je vaše aplikace nainstalovaná a aktivovaná. Pokud je vaše aplikace nakonfigurovaná tak, aby se nainstalovala na počítač uživatele z webu nebo ze sdílené síťové složky, může uživatel aplikaci aktivovat jenom jednou přes adresu URL. Potom bude uživatel obvykle aktivovat vaši aplikaci pomocí zástupce v nabídce **Start** . V důsledku toho je zaručeno, že aplikace získá argumenty řetězce dotazu pouze jednou během své životnosti. Pokud se rozhodnete tyto argumenty uložit v počítači uživatele pro budoucí použití, zodpovídáte za jejich uložení bezpečným a bezpečným způsobem.  
  
 Pokud je vaše aplikace online, bude vždy aktivována prostřednictvím adresy URL. I v tomto případě musí být aplikace zapsána, aby fungovala správně, pokud parametry řetězce dotazu chybí nebo jsou poškozené.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Povolte předávání parametrů adresy URL vaší [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikaci pouze v případě, že máte v úmyslu vyčistit vstup všech škodlivých znaků předtím, než je použijete. Řetězec, který je vložený pomocí uvozovek, lomítka nebo středníků, může například provádět libovolné operace s daty, pokud se používá nefiltrovaný dotaz SQL na databázi. Další informace o zabezpečení řetězce dotazů najdete v tématu [Přehled zneužití skriptů](https://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečování aplikací ClickOnce](../deployment/securing-clickonce-applications.md)
