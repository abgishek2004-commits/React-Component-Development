# React Component Library Assignment

A clean and scalable React component library built with TypeScript, Tailwind CSS, and Storybook. This project implements two production-ready components: InputField and DataTable.

## Features

### InputField Component
- **Variants**: outlined, filled, ghost
- **Sizes**: small (sm), medium (md), large (lg)
- **States**: normal, loading, error, disabled
- **Features**: 
  - Password toggle visibility
  - Clear button functionality
  - Form validation states
  - Accessibility support (ARIA labels)
  - TypeScript with comprehensive prop interfaces

### DataTable Component
- **Core Features**:
  - Display tabular data with type-safe columns
  - Column sorting (ascending, descending, none)
  - Row selection (single/multiple)
  - Loading state with skeleton animation
  - Empty state with custom messaging
  - Custom render functions for cells
  - Responsive design

## Tech Stack

- **React 18** with TypeScript
- **Tailwind CSS** for styling
- **Storybook** for component documentation
- **Jest & React Testing Library** for testing
- **Vite** for fast development
- **Wouter** for routing

## Installation & Setup

1. **Install dependencies**:
   ```bash
   npm install
   ```

2. **Start development server**:
   ```bash
   npm run dev
   ```
   The application will be available at `http://localhost:5000`

3. **Start Storybook** (if configured):
   ```bash
   npm run storybook
   ```
   Storybook will be available at `http://localhost:6006`

4. **Run tests**:
   ```bash
   npm test
   ```

## Project Structure

```
├── client/
│   ├── src/
│   │   ├── components/
│   │   │   ├── InputField.tsx       # Main InputField component
│   │   │   ├── DataTable.tsx        # Main DataTable component
│   │   │   └── ui/                  # shadcn/ui components
│   │   ├── pages/
│   │   │   ├── home.tsx             # Demo showcase page
│   │   │   └── storybook.tsx        # Interactive Storybook page
│   │   ├── stories/
│   │   │   ├── InputField.stories.tsx
│   │   │   └── DataTable.stories.tsx
│   │   ├── __tests__/
│   │   │   ├── InputField.test.tsx
│   │   │   └── DataTable.test.tsx
│   │   └── lib/
│   │       └── test-utils.tsx       # Testing utilities
│   └── index.html
├── .storybook/                      # Storybook configuration
├── server/                          # Express backend (demo support)
├── shared/                          # Shared types and schemas
└── README.md
```

## Component APIs

### InputField

```tsx
interface InputFieldProps {
  value?: string;
  onChange?: (e: React.ChangeEvent<HTMLInputElement>) => void;
  label?: string;
  placeholder?: string;
  helperText?: string;
  errorMessage?: string;
  disabled?: boolean;
  invalid?: boolean;
  variant?: 'filled' | 'outlined' | 'ghost';
  size?: 'sm' | 'md' | 'lg';
  loading?: boolean;
  clearable?: boolean;
  passwordToggle?: boolean;
}
```

### DataTable

```tsx
interface DataTableProps<T> {
  data: T[];
  columns: Column<T>[];
  loading?: boolean;
  selectable?: boolean;
  onRowSelect?: (selectedRows: T[]) => void;
  selectedRows?: T[];
  emptyMessage?: string;
  onSort?: (key: string, direction: 'asc' | 'desc' | null) => void;
}

interface Column<T> {
  key: string;
  title: string;
  dataIndex: keyof T;
  sortable?: boolean;
  render?: (value: any, record: T, index: number) => React.ReactNode;
  align?: 'left' | 'center' | 'right';
}
```
## Usage Examples

### InputField Examples

```tsx
import InputField from '@/components/InputField';

<InputField
  label="Email"
  placeholder="Enter your email"
  type="email"
/>

<InputField
  label="Password"
  type="password"
  passwordToggle
  errorMessage="Password is required"
  invalid
/>

<InputField
  label="Search"
  placeholder="Type to search..."
  clearable
  variant="ghost"
/>
```

### DataTable Examples

```tsx
import DataTable from '@/components/DataTable';

const columns = [
  {
    key: 'name',
    title: 'Name',
    dataIndex: 'name',
    sortable: true,
  },
  {
    key: 'email',
    title: 'Email',
    dataIndex: 'email',
    sortable: true,
  },
  {
    key: 'status',
    title: 'Status',
    dataIndex: 'status',
    render: (value) => (
      <Badge variant={value === 'active' ? 'default' : 'secondary'}>
        {value}
      </Badge>
    ),
  },
];


<DataTable data={users} columns={columns} />


<DataTable
  data={users}
  columns={columns}
  selectable
  selectedRows={selectedUsers}
  onRowSelect={setSelectedUsers}
/>


<DataTable
  data={[]}
  columns={columns}
  loading={true}
/>
```

## Styling & Theming

The components use Tailwind CSS with CSS custom properties for consistent theming:

- **Design System**: Built on shadcn/ui design tokens
- **Color Scheme**: Supports light/dark mode
- **Responsive**: Mobile-first responsive design
- **Accessibility**: WCAG compliant with proper ARIA labels

## Features Checklist

### InputField Component
- Text input with label, placeholder, helper text, error message
- States: disabled, invalid, loading
- Variants: filled, outlined, ghost
- Sizes: small, medium, large
- Clear button functionality
- Password toggle
- TypeScript with proper typing
- Accessibility support

### DataTable Component
- Display tabular data
- Column sorting
- Row selection (single/multiple)
- Loading state
- Empty state
- Custom render functions
- TypeScript with generics
- Responsive design

### General Requirements
- TypeScript with proper typing
- Responsive design
- Basic accessibility (ARIA labels)
- Clean, modern styling
- Comprehensive test coverage
- Storybook documentation
- Demo/example usage

## Testing

The components are thoroughly tested with Jest and React Testing Library:

```bash

npm test


npm run test:watch
```

Test coverage includes:
- Component rendering
- User interactions
- State management
- Accessibility features
- Edge cases

## Documentation

- **Live Demo**: Available at `/` route showing all component features
- **Storybook**: Interactive component documentation
- **TypeScript**: Full type definitions for all props and interfaces

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## Build & Deployment

```bash

npm run build


npm run build-storybook
```

## License

MIT License - feel free to use this code for your projects.

---
