---
title: Lambda 表达式不是有效的第一个表达式中&#39;Select Case&#39;语句
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: c492615850ec089fe35c1ae4eaba90a741e30f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588916"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Lambda 表达式不是有效的第一个表达式中&#39;Select Case&#39;语句
不能使用 lambda 表达式中的测试表达式`Select Case`语句。 Lambda 表达式定义返回函数和的测试表达式`Select Case`语句必须是基本数据类型。  
  
 下面的代码会导致此错误：  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **错误 ID:** BC36635  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
-   检查你的代码以确定是否可以使用其他条件构造，例如 `If...Then...Else` 语句。  
  
-   你可能具有想要调用函数，如下面的代码中所示：  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>请参阅  
 [Lambda 表达式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [If...Then...Else 语句](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Select...Case 语句](../../../visual-basic/language-reference/statements/select-case-statement.md)
