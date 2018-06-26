# **Viết code nghệ thuật**
  
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/d8lgpfshcr_logo.jpg)

_Bài viết tham khảo nội dung và hình ảnh từ hai cuốn sách gối đầu giường của dev,  **[Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)**  và  **[Code Complete](https://www.amazon.com/Code-Complete-Practical-Handbook-Construction/dp/0735619670)**, nếu có thời gian thì các bạn có thể tìm đọc thêm, rất hữu ích._

## Mở đầu

Cách đây khoảng mấy chục năm, có lẽ điều quan trọng nhất khi bạn code chỉ là sự hiệu quả và tối ưu. Khi đó RAM của máy tính còn được tính bằng byte thay vì giggabyte, tài nguyên hạn hẹp đến mức mỗi lúc máy tính chỉ có thể chạy một chương trình. Những ngày đó đã xa rồi.

Cùng với tốc độ phát triển nhanh chóng của phần cứng, tính hiệu quả tụt lại phía sau và nhường chỗ cho một yếu tố quan trọng hơn, viết code đẹp, dễ đọc và dễ hiểu. Điều này xuất phát từ thực tiễn là quy mô của các project trở nên lớn hơn, các mô hình Agile đòi hỏi sự cộng tác giữa mọi người nhiều hơn, môi trường và requirement thay đổi nhanh chóng đòi hỏi code phải dễ dàng thay đổi và bảo trì.

Tuy nhiên, khi mới bắt đầu chúng ta thường có thiên hướng viết code xấu. Có thể vì lười, hoặc có thể bạn nghĩ không có đủ thời gian để làm công việc tốt hơn, rằng boss sẽ tức giận vì bạn dành quá nhiều thời gian để viết code đẹp hơn. Cũng có thể bạn quá mệt mỏi khi viết một chương trình nào đó và chỉ muốn làm cho xong thôi. Và thế là những đống code thập cẩm ra đời.

Những lúc nhìn lại đống code đó, chúng ta lại muốn để lại đến ngày hôm sau. Chúng ta thở phào nhẹ nhõm khi thấy chương trình vẫn hoạt động bình thường, và cho rằng một đống code lộn xộn mà chạy được vẫn tốt hơn là không có gì. Tất cả đều ổn cho đến ngày bug xuất hiện, hoặc khách hàng ngẫu hứng muốn thêm một vài thay đổi để ứng dụng ngầu hơn. Và mọi rắc rối bắt đầu.

**Thế nào là code đẹp**

Viết code đẹp đòi hỏi chúng ta phải hình thành được  **cảm giác**  về code,  **cảm giác**  về tính sạch đẹp của nó (code-sense). Có những người sinh ra đã có cảm giác này rồi, những người khác phải luyện tập và học hỏi mới đạt được. Nó không chỉ giúp chúng ta nhìn ra một đoạn code là tốt hay xấu, mà còn cho chúng ta thấy những phương pháp, cách thức để biến code xấu thành code đẹp.

> _Tôi muốn code của mình phải tinh tế và hiệu quả. Logic phải rõ ràng để bug không thể ẩn nấp được, sự phụ thuộc lẫn nhau giữa các thành phần được tối thiểu hoá để bảo trì dễ hơn, hiệu năng gần như tối ưu để không khiến người khác làm code lộn xộn bằng những đoạn tối ưu không có quy tắc. Code đẹp là code làm một việc tốt._
> 
> **Bjarne Stroustrup**, inventor of  **C++ and author of The C++ Programming Language**
> 
> _Code đẹp là code đơn giản và ý đồ rõ ràng. Code đẹp đọc như một đoạn văn hay. Code đẹp không làm mơ hồ ý đồ của người viết, ngược lại là sự kết hợp của sự trừu tượng hoá và những câu lệnh điều khiển rõ ràng._
> 
> **Grady Booch**, author of  **Object Oriented Analysis and Design with Applications**
> 
> _Code đẹp là code có thể đọc và cải thiện bởi những người khác. Có unit test và acceptance test. Code đẹp dùng cách đặt tên có nghĩa, cung cấp một cách xử lý duy nhất cho mỗi mục đích, sự phụ thuộc lẫn nhau được tối thiểu hoá, cung cấp API rõ ràng và đơn giản._
> 
> **“Big” Dave Thomas**, founder of OTI, godfather of the Eclipse strategy

## Để viết code đẹp hơn

Giới thiệu dài dòng đủ rồi, sau đây chúng ta sẽ đi vào phần chính. Các quy tắc sẽ được trình bày một cách ngắn gọn nhất có thể, kèm với ví dụ.

### 1. Đặt tên có nghĩa

![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/klzsd0p55i_MeaningfulNames.PNG)

#### Sử dụng tên thể hiện rõ ý đồ

Chọn tên đúng có thể mất thời gian suy nghĩ, nhưng đảm bảo sẽ tiết kiệm cho bạn nhiều thời gian hơn về lâu dài. Vì thế nên chọn tên cẩn thận và đổi tên khi bạn tìm được từ tốt hơn.

Tên của biến, hàm hoặc class phải nói lên vì sao nó tồn tại, nó làm gì và được sử dụng như thế nào. Nếu tên biến cần phải chú thích mới hiểu được, đó là tên chưa thể hiện được ý đồ.

Tên biến chưa tốt:

```
int d; // elapsed time in days

```

Tên biến tốt:

```
int elapsedTimeInDays;
int daysSinceCreation;
int daysSinceModification;
int fileAgeInDays;

```

#### Sử dụng tên có thể phát âm được, tìm kiếm được

Tìm kiếm dễ dàng và nhớ nhanh hơn.

Sử dụng:

```
class Customer {
  private Date generationTimestamp;
  private Date modificationTimestamp;;
  private final String recordId = "102";
  /* ... */
};

```

Thay vì:

```
class DtaRcrd102 {
  private Date genymdhms;
  private Date modymdhms;
  private final String pszqint = "102";
  /* ... */
};

```

#### Tránh mã hoá

Mã hoá tên biến chỉ làm chúng ta mất công giải mã. Một ví dụ về mã hoá tên phổ biến trước đây là  **`Hungarian Notation`**, được thực hiện bằng cách thêm một vài chữ cái biểu thị kiểu ngay trước tên biến, ví dụ  `txtName, iAge...`

Điều này đặc biệt đúng với Java, là một ngôn ngữ có quy định chặt chẽ về kiểu. Các công cụ phát triển (IDE) cũng đã đủ mạnh để highlight các biến quan trọng và có thể phát hiện các lỗi về kiểu ngay từ khi chưa biên dịch code. Vì thế mã hoá chỉ làm việc đổi tên biến, hàm, class trở nên khó hơn. Đồng thời việc đọc code cũng vướng víu hơn.

```
PhoneNumber phoneString;
// name not changed when type changed!

```

#### Tránh mental mapping

Hạn chế việc người đọc code phải dịch tên bạn đặt ra sang một tên khác mà họ biết. Vấn đề này có thể xảy ra khi bạn sử dụng những tên không nằm trong domain của bài toán đặt ra, hoặc sử dụng tên khác với tư duy thông thường.

Ví dụ rõ nhất là đặt tên biến chỉ có một chữ cái và sử dụng các hằng số magic. Ví dụ:

```
int i, j;  
int secondsInADay = 24 * 60 * 60;

```

Viết lại đoạn trên một cách rõ ràng hơn:

```
static final int SECONDS_IN_A_MINUTE = 60;
static final int MINUTES_IN_AN_HOUR = 60;
static final int HOURS_IN_A_DAY = 24;

int numberOfEmployees, numberOfRooms;
int secondsInADay = HOURS_IN_A_DAY * MINUTES_IN_AN_HOUR * SECONDS_IN_A_MINUTE;

```

#### Tên class

Class và đối tượng nên có tên là danh từ hoặc cụm danh từ như  `Customer`,  `WikiPage`,  `Account`. Hạn chế các từ như  `Manager`,  `Processor`,  `Data`  hoặc  `Info`  khi đặt tên class và đối tượng.

#### Tên hàm

Tền hàm nên được đặt bằng động từ hoặc cụm động từ như  `postPayment`,  `deletePage`  hoặc  `save`.

Khi overload constructor, sử dụng hàm static với tên thể hiện mối liên hệ với tham số. Ví dụ:

```
Complex fulcrumPoint = Complex.FromRealNumber(23.0);

```

sẽ tốt hơn là:

```
Complex fulcrumPoint = new Complex(23.0);

```

### 2. Hàm

![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/f43qmi7kef_Functions.PNG)

#### Ngắn gọn và làm một việc duy nhất

Hàm phải ngắn hết mức có thể. Một hàm lý tưởng viết không quá 20 dòng. Về nguyên tắc, nếu hàm quá dài hãy chia nhỏ thành các hàm con, mỗi hàm con thực hiện một việc duy nhất. Tên của hàm phải thể hiện rõ tác dụng duy nhất của nó.

```
public static String renderPage(PageData pageData, boolean isSuite) {
  if (isTestPage(pageData))
    includeSetupAndTeardownPages(pageData, isSuite);
  return pageData.getHtml();
}

```

#### Tham số

Số lượng tham số lý tưởng của một hàm không nên quá 2. Khi số lượng tham số nhiều, xem xét việc đóng gói các tham số liên quan thành class thích hợp. Ví dụ:

```
Circle makeCircle(double x, double y, double radius);
Circle makeCircle(Point center, double radius);

```

Không nên sử dụng tham số ra (output argument), điều này sẽ gây sự mập mờ khó hiểu. Vì chúng ta đã quen với việc truyền thông tin vào hàm qua tham số và nhận lại kết quả qua  `return`.

#### Không có tác dụng phụ

Hàm không nên thực hiện bất kỳ một việc nào khác ngoài nội dung thể hiện qua tên của nó. Như thế sẽ gây những lỗi khó hiểu do hàm thực hiện các hành vi ngoài hiểu biết của người dùng.

Hàm  `checkPassword`  dưới đây vi phạm điều này, bởi vì nó gọi  `Session.initialize()`. Từ tên hàm chúng ta chỉ biết nó kiểm tra password, không hề có một gợi ý nào là nó sẽ khởi tạo session cả.

```
public class UserValidator {

  private Cryptographer cryptographer;

  public boolean checkPassword(String userName, String password) {
    User user = UserGateway.findByName(userName);
    if (user != User.NULL) {
      String codedPhrase = user.getPhraseEncodedByPassword();
      String phrase = cryptographer.decrypt(codedPhrase, password);
      if ("Valid Password".equals(phrase)) {
        Session.initialize();
        return true;
      }
    }
    return false;
  }
}

```

Có thể bạn sẽ muốn sửa lại tên hàm thành  `checkPasswordAndInitializeSession`, tuy nhiên rõ ràng điều này vi phạm nguyên tắc  _mỗi hàm chỉ thực hiện duy nhất một việc_.

#### Tách biệt giữa hành động và truy vấn

Mỗi hàm chỉ nên thực hiện hành động hoặc trả lời câu hỏi. Thực hiện cả hai sẽ gây khó hiểu cho người đọc. Ví dụ:

```
public boolean set(String attribute, String value);

```

Hàm này thực hiện set value cho một thuộc tính, trả về  `true`  nếu thành công và  `false`  nếu thất bại. Điều này sẽ dẫn đến cách dùng dễ gây nhầm lẫn về ý đồ như sau:

```
if (set("username", "unclebob"))...

```

#### Don't Repeat Yourself DRY

Luôn tách các đoạn code giống nhau thành các hàm riêng biệt để có thể dễ dàng sử dụng lại và bảo trì.

### 3. Comment

![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/ofreb3gzyw_comment.PNG)

#### Comment không thể chữa code xấu

Một trong những động cơ để viết comment là do viết code không tốt. Khi bạn viết một module nào đó và thấy nó khó hiểu và không có tổ chức. Thế nên bạn tự nói với chính mình "À mình phải comment phần này cho dễ hiểu hơn". Đừng làm thế, tốt hơn hết là hãy viết lại code.

Code rõ ràng, dễ hiểu với ít comment tốt hơn nhiều so với code phức tạp, rối rắm với nhiều comment. Thay vì mất thời gian viết comment giải thích code, hãy dành thời gian viết lại code.

Ví dụ, viết

```
if (employee.isEligibleForFullBenefits()) {}

```

thay vì

```
// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) && (employee.age > 65)) {}

```

Thay comment bằng các hàm và tên biến thể hiện rõ ý đồ bạn muốn.

#### Comment code không dùng

Có những lúc bạn thấy một đoạn code nào đó không dùng đến nữa, bạn comment đoạn đó đi vì nghĩ sau này có thể dùng lại. Đừng làm thế, hãy xoá nó đi, sử dụng các source control như  **Git**  thì bạn có thể xem lại lịch sử bất kỳ lúc nào. Đoạn comment đó chỉ làm việc đọc code thêm rối rắm.

### 4. Định dạng

#### Độ mở theo chiều dọc giữa các nhóm code

Hầu như code đều được đọc từ trái sang phải và từ trên xuống dưới. Mỗi dòng thể hiện một diễn đạt nhất định, mỗi nhóm các dòng thế hiện một suy nghĩ, một sự liên quan nhất định đến nhau. Các suy nghĩ đó nên được tách biệt với nhau bằng một khoảng trắng.

Ví dụ

```
package fitnesse.wikitext.widgets;

import java.util.regex.*;

public class BoldWidget extends ParentWidget {
  public static final String REGEXP = "'''.+?'''";
  private static final Pattern pattern = Pattern.compile("'''(.+?)'''",
        Pattern.MULTILINE + Pattern.DOTALL
  );

  public BoldWidget(ParentWidget parent, String text) throws Exception {
    super(parent);
    Matcher match = pattern.matcher(text);
    match.find();
    addChildWidgets(match.group(1));
  }

  public String render() throws Exception {
    StringBuffer html = new StringBuffer("<b>");
    html.append(childHtml()).append("</b>");
    return html.toString();
  }
}

```

sẽ rõ ràng hơn là

```
package fitnesse.wikitext.widgets;
import java.util.regex.*;
public class BoldWidget extends ParentWidget {
  public static final String REGEXP = "'''.+?'''";
  private static final Pattern pattern = Pattern.compile("'''(.+?)'''",
        Pattern.MULTILINE + Pattern.DOTALL
  );
  public BoldWidget(ParentWidget parent, String text) throws Exception {
    super(parent);
    Matcher match = pattern.matcher(text);
    match.find();
    addChildWidgets(match.group(1));
  }
  public String render() throws Exception {
    StringBuffer html = new StringBuffer("<b>");
    html.append(childHtml()).append("</b>");
    return html.toString();
  }
}

```

#### Khoảng cách giữa các thành phần liên quan

Các thành phần có mối liên quan mật thiết với nhau nên được đặt gần nhau. Tránh trường hợp bạn phải chạy từ file này sang file khác, cuộn lên cuộn xuống chỉ để xem các hàm gọi đến nhau như thế nào.

##### Khai báo biến

Biến nên được khai báo gần vị trí sử dụng hết mức có thể. Vì hàm rất ngắn nên khai báo có thể đặt ở đầu hàm.

Các thuộc tính của class nên được khai báo ở đầu class để đảm bảo nhất quán.

##### Các hàm phụ thuộc

Nếu một hàm gọi một hàm khác, chúng nên nằm gần nhau. Hàm được gọi nằm ngay dưới hàm gọi. Điều này giúp cho việc tìm kiếm hàm và đọc hiểu chương trình dễ hơn, tự nhiên hơn.

Ví dụ:

```
public class WikiPageResponder implements SecureResponder {

  protected WikiPage page;
  protected PageData pageData;
  protected String pageTitle;
  protected Request request;
  protected PageCrawler crawler;

  public Response makeResponse(FitNesseContext context, Request request) throws Exception {
    String pageName = getPageNameOrDefault(request, "FrontPage");
    loadPage(pageName, context);
    if (page == null)
      return notFoundResponse(context, request);
    else
      return makePageResponse(context);
  }

  private String getPageNameOrDefault(Request request, String defaultPageName) {
    String pageName = request.getResource();
    if (StringUtil.isBlank(pageName))
      pageName = defaultPageName;
    return pageName;
  }

  protected void loadPage(String resource, FitNesseContext context) throws Exception {
    WikiPagePath path = PathParser.parse(resource);
    crawler = context.root.getPageCrawler();
    crawler.setDeadEndStrategy(new VirtualEnabledPageCrawler());
    page = crawler.getPage(context.root, path);
    if (page != null)
      pageData = page.getData();
  }

  private Response notFoundResponse(FitNesseContext context, Request request) throws Exception {
    return new NotFoundResponder().makeResponse(context, request);
  }

  private SimpleResponse makePageResponse(FitNesseContext context) throws Exception {
    pageTitle = PathParser.render(crawler.getFullPath(page));
    String html = makeHtml(context);
    SimpleResponse response = new SimpleResponse();
    response.setMaxAge(0);
    response.setContent(html);
    return response;
  }
}

```

#### Định dạng theo chiều ngang

Số ký tự tối đa trên mỗi dòng nên được giới hạn, thông thường bé hơn 120 ký tự.
### 5. Statement

#### Tổ chức code theo đường thẳng

Đối với các mệnh đề phải được sắp xếp theo một thứ tự nhất định để đảm bảo hoạt động đúng, sử dụng các biến và tham sổ hàm, cũng như cách đặt tên phù hợp để thể hiện mối tương quan:

```
data = ReadData();
results = CalculateResultsFromData( data );
PrintResults( results );

```

Ở đây,  `data`  phải được đọc trước khi xử lý sinh ra  `results`, và  `results`  phải được tính toán trước khi in ra màn hình. Ba mệnh đề này có mối liên quan chặt chẽ và bắt buộc nó phải được tổ chức theo một thứ tự nhất định.

Ngược lại trong ví dụ sau, mối liên quan thứ tự đã bị ẩn đi, khiến người gọi có thể bị nhầm lẫn:

```
revenue.ComputeMonthly();
revenue.ComputeQuarterly();
revenue.ComputeAnnual();

```

Việc tính lợi nhuận theo năm phụ thuộc vào lợi nhuận theo quý đã được tính trước, và lợi nhuận theo quý phụ thuộc vào lợi nhuận theo tháng. Tuy nhiên không có cơ chế nào để bắt người sử dụng gọi các hàm này theo đúng thứ tự.

Đối với các mệnh đề mà thứ tự của chúng không ảnh hưởng đến logic, cần tổ chức sao cho việc tìm kiếm thông tin và đọc hiểu thông tin là dễ nhất. Nguyên tắc là sắp xếp code sao cho chương trình có thể đọc mượt mà liên tục từ trên xuống dưới, không cần nhảy linh tinh, cuộn lên cuộn xuống để xem hàm này cài đặt như thế nào, biến này khai báo ở đâu...

Xét ví dụ sau:

```
MarketingData marketingData;
SalesData salesData;
TravelData travelData;

travelData.ComputeQuarterly();
salesData.ComputeQuarterly();
marketingData.ComputeQuarterly();

salesData.ComputeAnnual();
marketingData.ComputeAnnual();
travelData.ComputeAnnual();

salesData.Print();
travelData.Print();
marketingData.Print();

```

Nhìn qua thì có vẻ code được tổ chức rất gọn gàng và logic. Nhưng giả sử chúng ta muốn biết  `marketingData`được tính như thế nào. Bạn phải đi từ dòng cuối cùng và duyệt lên hết đến đầu mã nguồn, ghi nhớ xem ở từng vị trí dữ liệu được xử lý ra làm sao, rất khó khăn.

Tổ chức code lại sao cho các mệnh đề liên quan được gom nhóm với nhau sẽ cải thiện việc đọc hiểu rất nhiều.

```
MarketingData marketingData;
marketingData.ComputeQuarterly();
marketingData.ComputeAnnual();
marketingData.Print();

SalesData salesData;
salesData.ComputeQuarterly();
salesData.ComputeAnnual();
salesData.Print();

TravelData travelData;
travelData.ComputeQuarterly();
travelData.ComputeAnnual();
travelData.Print();

```

#### Mệnh đề  _if_

Tổ chức sao cho trường hợp bình thường được xử lý trước, sau đó mới đến các trường hợp ngoại lệ. Ví dụ sau vi phạm quy tắc này:

```
OpenFile( inputFile, status )
If ( status = Status_Error ) Then
  errorType = FileOpenError
Else
  ReadFile( inputFile, fileData, status )
  If ( status = Status_Success ) Then
    SummarizeFileData( fileData, summaryData, status )
    If ( status = Status_Error ) Then
      errorType = ErrorType_DataSummaryError
    Else
      PrintSummary( summaryData )
      SaveSummaryData( summaryData, status )
      If ( status = Status_Error ) Then
        errorType = ErrorType_SummarySaveError
      Else
        UpdateAllAccounts()
        EraseUndoFile()
        errorType = ErrorType_None
      End If
    End If
  Else
    errorType = ErrorType_FileReadError
  End If
End If

```

Code này rất khó đọc vì phần xử lý lỗi và phần xử lý bình thường lẫn với nhau, rất khó có thể đọc được xem trong trường hợp bình thường thì code được chạy như thế nào.

Đoạn code sau đây viết lại theo cách dễ hiểu hơn:

```
OpenFile( inputFile, status )
If ( status = Status_Success ) Then
  ReadFile( inputFile, fileData, status )
  If ( status = Status_Success ) Then
    SummarizeFileData( fileData, summaryData, status )
    If ( status = Status_Success ) Then
      PrintSummary( summaryData )
      SaveSummaryData( summaryData, status )
      If ( status = Status_Success ) Then
        UpdateAllAccounts()
        EraseUndoFile()
        errorType = ErrorType_None
      Else
        errorType = ErrorType_SummarySaveError
      End If
    Else
      errorType = ErrorType_DataSummaryError
    End If
  Else
    errorType = ErrorType_FileReadError
  End If
Else
  errorType = ErrorType_FileOpenError
End If

```

Đối với các mệnh đề if-then-else liên tục nhau, xét ví dụ:

```
if ( inputCharacter < SPACE ) {
    characterType = CharacterType_ControlCharacter;
}
else if (
    inputCharacter == ' ' ||
    inputCharacter == ',' ||
    inputCharacter == '.' ||
    inputCharacter == '!' ||
    inputCharacter == '(' ||
    inputCharacter == ')' ||
    inputCharacter == ':' ||
    inputCharacter == ';' ||
    inputCharacter == '?' ||
    inputCharacter == '-'
) {
    characterType = CharacterType_Punctuation;
}
else if ( '0' <= inputCharacter && inputCharacter <= '9' ) {
    characterType = CharacterType_Digit;
}
else if (
    ( 'a' <= inputCharacter && inputCharacter <= 'z' ) ||
    ( 'A' <= inputCharacter && inputCharacter <= 'Z' )
) {
    characterType = CharacterType_Letter;
}

```

Thay thế các mệnh đề test phức tạp bằng các hàm tương ứng:

```
if ( IsControl( inputCharacter ) ) {
    characterType = CharacterType_ControlCharacter;
}
else if ( IsPunctuation( inputCharacter ) ) {
    characterType = CharacterType_Punctuation;
}
else if ( IsDigit( inputCharacter ) ) {
    characterType = CharacterType_Digit;
}
else if ( IsLetter( inputCharacter ) ) {
    characterType = CharacterType_Letter;
}

```

Đưa trường hợp phổ biến lên trước, ví dụ nếu chữ cái thông thường là phổ biến nhất thì ta tổ chức lại như sau:

```
if ( IsLetter( inputCharacter ) ) {
    characterType = CharacterType_Letter;
}
else if ( IsPunctuation( inputCharacter ) ) {
    characterType = CharacterType_Punctuation;
}
else if ( IsDigit( inputCharacter ) ) {
    characterType = CharacterType_Digit;
}
else if ( IsControl( inputCharacter ) ) {
    characterType = CharacterType_ControlCharacter;
}

```

Đảm bảo rằng tất cả các trường hợp đều được xử lý, kể cả những trường hợp bạn không có ý định cài đặt:

```
if ( IsLetter( inputCharacter ) ) {
    characterType = CharacterType_Letter;
}
else if ( IsPunctuation( inputCharacter ) ) {
    characterType = CharacterType_Punctuation;
}
else if ( IsDigit( inputCharacter ) ) {
    characterType = CharacterType_Digit;
}
else if ( IsControl( inputCharacter ) ) {
    characterType = CharacterType_ControlCharacter;
}
else {
    DisplayInternalError( "Unexpected type of character detected." );
}

```

#### Mệnh đề  _case_

Giữ cho phần code trong mỗi case ngắn gọn. Nếu có thể hay thay thế nó bằng một hàm nào đó.

```
action = userCommand[ 0 ];
switch ( action ) {
  case 'c':
    Copy();
    break;
  case 'd':
    DeleteCharacter();
    break;
  case 'f':
    Format();
    break;
  case 'h':
    Help();
    break;
    ...
  default:
    HandleUserInputError( ErrorType.InvalidUserCommand );
}

```

Một số lời khuyên khi sắp xếp thứ tự của các case:

-   Sắp xếp theo thứ tự bảng chữ cái: Nếu vai trò của mỗi case là như nhau, sắp theo thứ tự này làm code dễ đọc hơn và việc tìm một case cụ thể dễ hơn.
-   Để các case thường dùng lên đầu tiên: Người đọc có thể tìm các case thường được thực thi nhất một cách nhanh chóng.
-   Để các case bình thường lên trước: Trong trường hợp bạn có một số case xử lý flow thông thường và một số case xử lý ngoại lệ, để case thông thường lên trước. Thêm comment chỉ rõ case nào là bình thường, case nào xử lý ngoại lệ.

Kết thúc mỗi case bắt buộc phải có break, trong trường hợp thật sự cần thiết phải bỏ qua thì bạn cần comment lại rõ ràng lý do tại sao cần code như thế:

```
switch ( errorDocumentationLevel ) {
  case DocumentationLevel_Full:
    DisplayErrorDetails( errorNumber );
    // FALLTHROUGH -- Full documentation also prints summary comments
  case DocumentationLevel_Summary:
    DisplayErrorSummary( errorNumber );
    // FALLTHROUGH -- Summary documentation also prints error number
  case DocumentationLevel_NumberOnly:
    DisplayErrorNumber( errorNumber );
    break;
  default:
    DisplayInternalError( "Internal Error 905: Call customer support." );
}
```

==================================
==================================
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/3b90x8nuvb_System_design.PNG)

Design nói đến ở đây là thiết kế các thành phần của hệ thống phần mềm. Thiết kế tốt sẽ có những đặc tính sau, sẽ có những đánh đổi mà bạn phải cân nhắc cho phù hợp với hệ thống của mình, tuy nhiên nên cố gắng đạt được càng nhiều càng tốt:

-   **Độ phức tạp tối thiểu (Minimal complexity)**: Mục tiêu chính của thiết kế chính là giảm độ phức tạp của hệ thống. Tránh tạo ra những thiết kế "thông minh". Thiết kế "thông minh" thường khiến người dùng khó nắm bắt. Thay vào đó tập trung tạo các thiết kế "đơn giản" và "dễ hiểu". Nếu thiết kế của bạn không giúp bạn bỏ qua những thành phần khác của hệ thống khi đang tập trung làm bộ phận cụ thể, thì thiết kế đó chưa phải là một thiết kế tốt.
    
-   **Dễ bảo trì (Ease of maintenance)**: Dễ bảo trì có nghĩa là thiết kế với suy nghĩ của một lập trình viên "maintain". Tưởng tượng những câu hỏi mà lập trình viên bảo trì sẽ hỏi về đoạn code bạn đang viết. Hãy nghĩ đến lập trình viên bảo trì như khán giả của mình và thiết kế một hệ thống dễ hiểu.
    
-   **Ít liên kết (Loose coupling)**: Thiết kế sao cho mức liên kết giữa các thành phần của chương trình là tối thiểu. Sử dụng các nguyên tắc về trừu tượng hoá (abstraction), đóng gói (encapsulation), che giấu thông tin (information hiding) khi thiết kế class để đảm bảo mức liên kết ít nhất. Mức độ liên kết càng thấp thì càng tối thiểu hoá lượng công việc cần làm khi thực hiện tích hợp, test và bảo trì.
    
-   **Tính mở rộng (Extensibility)**: Bạn có thể cải tiến hệ thống mà không gây xáo trộn đến các cài đặt bên dưới. Bạn có thể thay một thành phần của hệ thống một cách dễ dàng mà không ảnh hưởng đến các thành phần khác.
    
-   **Tính tái sử dụng (Reusability)**: Thiết kế hệ thống sao cho có thể tải sử dụng các thành phần ở một hệ thống khác.
    
-   **Tính di động (Portability)**: Hệ thống có thể dễ dàng chuyển sang một môi trường hoạt động khác.
    
-   **Tính gọn gàng (Leanness)**: Thiết kế sao cho hệ thống không có những phần thừa. Một phần mềm hoàn chỉnh không phải là không còn gì có thể thêm vào được, mà là không có gì có thể bớt đi. Điều này thực sự quan trọng vì phần code thừa phải được review, test khi các thành phần khác thay đổi, nó làm tăng khối lượng công việc phải làm một cách vô ích.
    
-   **Tính phân tầng (Stratification)**: Hệ thống được trừu tượng hoá thành các tầng. Bạn có thể review hệ thống từ một tầng bất kì và có một cái nhìn nhất quán.
    

Ví dụ, nếu bạn viết một hệ thống hiện đại nhưng có sử dụng nhiều code cũ, code không được thiết kế tốt, hãy viết một module mới có vai trò cầu nối giữa code cũ và hệ thống đang phát triển. Các phần còn lại của hệ thống sẽ sử dụng các API chuẩn của module này thay vì tương tác trực tiếp với code cũ. Như thế tính xấu của code cũ sẽ được ẩn đi, và nếu chúng ta có cần refactor lại phần code cũ thì không ảnh hưởng gì đến hệ thống mới mà chỉ cần thay đổi một chút ở module cầu nối.

-   **Các kỹ thuật chuẩn (Standard techniques)**: Hệ thống không nên phụ thuộc quá nhiều vào các thành phần lạ, điều đó sẽ giảm bớt độ cực nhọc cho những người sau khi họ muốn nắm bắt cách vận hành của hệ thống. Cố gắng sử dụng những cách thức, module đã được chuẩn hoá và thông dụng nếu có thể.