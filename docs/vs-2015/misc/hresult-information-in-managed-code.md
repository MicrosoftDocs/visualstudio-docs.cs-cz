---
title: Informace o HRESULT ve spravovaném kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: douge
ms.openlocfilehash: 08d14f1155838e53321224280a69e7a76bf07b52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911847"
---
# <a name="hresult-information-in-managed-code"></a>Informace o HRESULT ve spravovaném kódu
Interakce mezi spravovaným kódem a modelu COM může způsobit potíže, pokud nedojde k vrácené hodnoty HRESULT.  
  
 V rozhraní modelu COM můžete přehrát návratovou hodnotu HRESULT pracovníci v těchto rolích:  
  
- Poskytování informací o chybách (například <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>).  
  
- Poskytovat informace o stavu týkající se chování normální programu.  
  
  Když COM volá do spravovaného kódu, může způsobit HRESULTs tyto problémy:  
  
- Funkce modelu COM, které vracejí hodnoty HRESULT menší než nula (Kódy selhání) generovat výjimky.  
  
- Metody modelu COM, které pravidelně vrací dva nebo více různých úspěch kódy, například <xref:Microsoft.VisualStudio.VSConstants.S_OK> nebo <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, nemůže být rozlišující.  
  
  Protože mnoho [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] buď vrátí hodnoty HRESULT menší než nula nebo návratové kódy různých úspěch, funkce modelu COM [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] sestavení vzájemné spolupráce být napsán tak, aby podpisy metod jsou zachovány. Všechny [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] spolupráce metody jsou `int` typu. Spolupráce vrstvy bez změny a bez generování událostí výjimky se předaly hodnoty HRESULT.  
  
  Protože funkce modelu COM vrátí HRESULT spravované metodě, která ho zavolá, musí volání metody zkontrolujte HRESULT a vyvolat výjimky podle potřeby.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Zpracování výsledky HRESULTs vracené z modelu COM pro spravovaný kód  
 Když zavoláte rozhraní modelu COM ze spravovaného kódu, zkontrolujte hodnotu HRESULT a vyvolat výjimku, pokud je to nutné. <xref:Microsoft.VisualStudio.ErrorHandler> Třída obsahuje <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> do něho předaný metodě, která se vyvolá výjimka modelu COM, v závislosti na hodnotu HRESULT.  
  
 Ve výchozím nastavení <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> vyvolá výjimku, pokaždé, když je jí předán HRESULT, který má hodnotu menší než nula. V případech, kdy přípustné hodnoty jsou tyto výsledky HRESULT a měla by být vyvolána žádná výjimka, by měly být předány hodnoty HRESULT Další <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po otestování hodnoty. Pokud hodnota HRESULT testován odpovídá všechny hodnoty HRESULT explicitně předán <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, není vyvolána žádná výjimka.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Třída obsahuje konstanty pro běžné HRESULT, například <xref:Microsoft.VisualStudio.VSConstants.S_OK> a <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULT, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> a <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> poskytuje také <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> a <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metody, které odpovídají úspěšné a NEÚSPĚŠNÉ makra v modelu COM.  
  
 Zvažte například následující volání funkce, ve kterém <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> je přijatelné vrácení hodnoty, ale jiné HRESULT menší než nula představuje chybu.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Pokud existuje více než jeden přijatelné návratové hodnoty, další hodnoty HRESULT lze připojit pouze k seznamu při volání funkce <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Vrací HRESULTS modelu COM ze spravovaného kódu  
 Pokud dojde k žádné výjimce, spravovaný kód vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkce modelu COM, která ji zavolala. Komunikace s objekty COM podporuje běžné výjimky, které jsou silně typované ve spravovaném kódu. Například metoda, která přijímá nepřijatelnou `null` vyvolá argument <xref:System.ArgumentNullException>.  
  
 Pokud si nejste jistí výjimek má vyvolat, ale vy víte HRESULT chcete vrátit do modelu COM, můžete použít <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodu pro příslušnou výjimku. Tento postup funguje i s nestandardní chybu, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pokusy o mapování hodnota HRESULT je do něho předaný silného typu výjimky. V případě nedostupnosti vyvolá k obecné výjimce modelu COM. místo. Výsledkem je hodnota HRESULT předání <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> ze spravovaného kódu, které se vrátí do funkce modelu COM, která ji zavolala.  
  
> [!NOTE]
>  Snížit výkon, výjimky, které slouží k označení neobvyklého podmínky. Podmínky, ke kterým dochází často by měla být zpracováván jako vložené, namísto vyvolané výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Spravovaná rozšíření VSPackages](../misc/managed-vspackages.md)   
 [Spolupráce s nespravovaným kódem](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Postupy: mapování výsledků HRESULT a výjimek](http://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Vytváření komponent COM pro interoperabilitu](http://msdn.microsoft.com/en-us/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Spravovaná rozšíření VSPackages](../misc/managed-vspackages.md)