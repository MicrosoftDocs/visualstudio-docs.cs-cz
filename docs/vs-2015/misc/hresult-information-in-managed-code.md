---
title: HRESULT – informace ve spravovaném kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, HRESULT information
- HRESULT, managed VSPackages
ms.assetid: 0795ee94-17a8-4327-bf57-27cd5e312a4c
caps.latest.revision: 29
manager: jillfra
ms.openlocfilehash: 4f80b575656c2d8b1740f217f2e144f89f254078
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681637"
---
# <a name="hresult-information-in-managed-code"></a>HRESULT – informace ve spravovaném kódu
Interakce mezi spravovaným kódem a modelem COM může způsobovat problémy při zjištění vrácených hodnot HRESULT.  
  
 V rozhraní modelu COM může návratová hodnota HRESULT přehrát tyto role:  
  
- Doručovat informace o chybě (například <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> ).  
  
- Doručovat informace o stavu normálního chování programu.  
  
  Při volání modelu COM do spravovaného kódu mohou tyto problémy způsobit HRESULTs:  
  
- Funkce modelu COM, které vracejí hodnoty HRESULT menší než nula (kódy selhání) generují výjimky.  
  
- Metody modelu COM, které pravidelně vracejí dva nebo více různých kódů úspěšnosti, například <xref:Microsoft.VisualStudio.VSConstants.S_OK> nebo <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> , nelze odlišit.  
  
  Vzhledem k tomu, že mnoho [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] funkcí modelu COM vrátí hodnoty HRESULT menší než nula nebo vrátí různé kódy úspěchu, [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] sestavení spolupráce byla zapsána tak, aby byly zachovány signatury metod. Všechny [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] metody spolupráce jsou `int` typu. Hodnoty HRESULT jsou předávány prostřednictvím vrstvy spolupráce bez nutnosti změny a bez generování výjimek.  
  
  Vzhledem k tomu, že funkce modelu COM vrátí hodnotu HRESULT spravované metodě, která je volá, metoda volání musí podle potřeby kontrolovat HRESULT a vyvolat výjimky.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Zpracování HRESULTs vrácených do spravovaného kódu z modelu COM  
 Při volání rozhraní modelu COM ze spravovaného kódu, prověřte hodnotu HRESULT a v případě potřeby vyvolejte výjimku. <xref:Microsoft.VisualStudio.ErrorHandler>Třída obsahuje <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodu, která VYVOLÁ výjimku com v závislosti na hodnotě HRESULT, která je předána do ní.  
  
 Ve výchozím nastavení <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> vyvolá výjimku, kdykoli je předána hodnota HRESULT, která má hodnotu menší než nula. V případech, kdy tyto HRESULTs jsou přijatelné hodnoty a žádná výjimka by měla být vyvolána, hodnoty dalších HRESULTs by měly být předány <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Po otestování hodnot. Pokud testovaný HRESULT odpovídá všem hodnotám HRESULT, které jsou explicitně předány do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> , není vyvolána žádná výjimka.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants>Třída obsahuje konstanty pro běžné HRESULTS, například a a <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] HRESULTS, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> a <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> poskytuje také <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> metody a <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> , které odpovídají úspěšným a neúspěšným makrům v modelu COM.  
  
 Zvažte například následující volání funkce, ve kterém <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> je přijatelné návratové hodnoty, ale jakákoli jiná hodnota HRESULT menší než nula představuje chybu.  
  
 [!code-csharp[VSSDKHRESULTInformation#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]  
  
 Pokud je k dispozici více než jedna přijatelná návratová hodnota, lze do seznamu v volání metody přidat pouze další hodnoty HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> .  
  
 [!code-csharp[VSSDKHRESULTInformation#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Vrácení HRESULTs do modelu COM ze spravovaného kódu  
 Pokud nedojde k žádné výjimce, spravovaný kód vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkci com, která ji volala. Zprostředkovatel komunikace s objekty COM podporuje běžné výjimky, které jsou silně typované ve spravovaném kódu. Například metoda, která přijímá nepřijatelný `null` argument <xref:System.ArgumentNullException> , vyvolá.  
  
 Pokud si nejste jistí, která výjimka má být vyvolána, ale víte, že HRESULT, kterou chcete vrátit do modelu COM, lze použít <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodu k vyvolání příslušné výjimky. To funguje i s nestandardní chybou, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pokusí se namapovat HRESULT předané na výjimku silného typu. Pokud to nemůže, vyvolá místo toho obecnou výjimku modelu COM. Konečný výsledek je, že hodnota HRESULT, kterou předáte <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> ze spravovaného kódu, se vrátí do funkce com, která ji zavolala.  
  
> [!NOTE]
> Výjimky budou mít vliv na ohrožení zabezpečení a jsou určeny k označení abnormálních podmínek programu. Podmínky, ke kterým dochází často, by měly být zpracovány jako vložené místo vyvolané výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Spravované VSPackage](../misc/managed-vspackages.md)   
 [Spolupráce s nespravovaným kódem](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)   
 [Postupy: mapování HRESULTs a Exceptions](https://msdn.microsoft.com/library/610b364b-2761-429d-9c4a-afbc3e66f1b9)   
 [Sestavování komponent modelu COM pro spoluprovozování](https://msdn.microsoft.com/7a2c657a-cfef-40f0-bed3-7c2c0ac4abdf)   
 [Spravované VSPackage](../misc/managed-vspackages.md)