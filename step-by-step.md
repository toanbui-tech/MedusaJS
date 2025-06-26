# MEDUSA JS
- Medusa là một nền tảng thương mại điện tử có tích hợp sẵn Framework để tùy chỉnh.
- Mục tiêu sử dụng: dev sẽ tùy chỉnh meudsajs để tạo ra 1 **marketplace** dạng **subscribers** (thời gian or lượt sử dụng)
## CORE
### 1. Commerce Modules
- Module cung cấp các chức năng thương mại cốt lõi tại: https://docs.medusajs.com/resources/commerce-modules
### 2. Framework
 - Tất cả các ứng dụng thương mại yêu cầu một số mức độ tùy biến. Vì vậy, điều quan trọng là chọn một nền tảng tạo điều kiện xây dựng các tùy chỉnh đó.
 - *Medusa Framework loại bỏ chi phí này bằng cách cung cấp các API và công cụ cấp thấp mạnh mẽ cho phép bạn xây dựng bất kỳ loại tùy chỉnh nào trực tiếp trong dự án Medusa của mình. Bạn có thể xây dựng các tính năng tùy chỉnh, sắp xếp các hoạt động và truy vấn dữ liệu liền mạch trên các hệ thống, mở rộng chức năng cốt lõi và tự động hóa các tác vụ trong ứng dụng Medusa của mình.*
#### 2.1 Khi sử dụng Medusa Framework, bạn có thể xây dựng các tùy chỉnh như:
- [Product Reviews](https://docs.medusajs.com/resources/how-to-tutorials/tutorials/product-reviews)
- [Deep integration with an ERP system](https://docs.medusajs.com/resources/recipes/erp)
- [CMS integration with seamless content retrieval](https://docs.medusajs.com/resources/integrations/guides/sanity)
- [Custom item pricing in the cart](https://docs.medusajs.com/resources/examples/guides/custom-item-price)
- [Automated restock notifications](https://docs.medusajs.com/resources/recipes/commerce-automation/restock-notification)
- [Re-usable payment provider integrations](https://docs.medusajs.com/resources/references/payment/provider)
#### 2.2 Framework Concepts and Tools
Phần này mình sẽ tập trung tuyệt đối, cố gắng hiểu và kết nối tất cả chúng lại với nhau.
##### 2.2.1 Medusa Container:
  - Medusa Container là một registry chứa các công cụ/framework và module thương mại được đăng ký khi khởi động ứng dụng Medusa. Nó hoạt động giống như một dependency injection container, giúp bạn dễ dàng truy cập các tài nguyên bất cứ đâu trong app mà không cần phải khai báo thủ công các phụ thuộc.
    ```js
    import {
      MedusaRequest,
      MedusaResponse,
    } from "@medusajs/framework/http"
    import {
      ContainerRegistrationKeys,
    } from "@medusajs/framework/utils"
    
    export const GET = async (
      req: MedusaRequest,
      res: MedusaResponse
    ) => {
      const query = req.scope.resolve(ContainerRegistrationKeys.QUERY)
    
      const { data: posts } = await query.graph({
        entity: "post",
        fields: ["id", "title"],
      })
    
      res.json({ posts })
    }
    ```
 - Khi bạn sử dụng phương thức Query.Graph, bạn đang chạy một truy vấn thông qua biểu đồ nội bộ mà ứng dụng Medusa tạo ra. Biểu đồ này thu thập các mô hình dữ liệu của tất cả các mô -đun trong ứng dụng của bạn, bao gồm các mô -đun thương mại và tùy chỉnh và xác định các mối quan hệ và liên kết giữa chúng.
   - List of Resources Registered in the Medusa Container:
   ```bash
   ContainerRegistrationKeys.CONFIG_MODULE
   ContainerRegistrationKeys.LOGGER
   ContainerRegistrationKeys.QUERY
   ContainerRegistrationKeys.LINK
   ContainerRegistrationKeys.MANAGER
   baseRepository
   ```
   - How to Resolve From the Medusa Container:
   ```bash
   Subscriber
   Scheduled Job
   Workflow Step
   Module Services and Loaders
   ```
- Modules
- Module Links
- Data Models
- API Routes
- Scheduled Jobs
- Query
- Workflows
- Events and Subscribers
- Plugins

### 3. A Customizable admin dashboard
    - 
    
